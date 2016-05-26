# apply

apply是一个非常好用的函数，可以让我们给一个函数预绑定多个参数并生成一个可直接调用的新函数，简化代码。
```javascript
async.apply(t.inc, 3);
// 等价于
function(callback) { t.inc(3, callback); }
```
```javascript
var t = {}
t.inc = function(n, callback, timeout) {
    timeout = timeout || 200;
    setTimeout(function() {
        callback(null, n+1);
    }, timeout);
}
t.fire = function(obj, callback, timeout) {
    timeout = timeout || 200;
    setTimeout(function() {
        callback(null, obj);
    }, timeout);
}

async.parallel([
    function(callback) { t.inc(3, callback); }
    function(callback) { t.fire(100, callback); }
], function (err, results) {
    log('1.1 err: ', err);
    log('1.1 results: ', results);
});


async.parallel([
    async.apply(t.inc, 3),
    async.apply(t.fire, 100)
], function (err, results) {
    log('1.1 err: ', err);
    log('1.1 results: ', results);
});

//1.1 err: null
//1.1 results: [ 4, 100 ]
```

# applyEach

applyEach，可以实现给一数组中每个函数传相同参数，通过callback返回。
如果只传第一个参数，将返回一个函数对象

```javascript
async.applyEach([
    function (name,cb) {
        setTimeout(function () {
            log("1.1 handler: " + name + " A");
            cb(null, name);
        }, 500);
    }, function (name,cb) {
        setTimeout(function () {
            log("1.1 handler: " + name + " B");
            cb(null, name);
        }, 150);
    }
], 'Hello', function (err) {
    log('1.1 err: ', err);
});

//06.739> 1.1 handler: Hello B
//07.079> 1.1 handler: Hello A
//07.080> 1.1 err: null
```

# applyEachSeries

applyEachSeries与applyEach唯一不同的是，数组的函数同步执行。

```javascript
async.applyEachSeries([
    function (name,cb) {
        setTimeout(function () {
            log("1.3 handler: " + name + " A");
            cb(null, name);
        }, 500);
    }, function (name,cb) {
        setTimeout(function () {
            log("1.3 handler: " + name + " B");
            cb(null, name);
        }, 150);
    }
], "aaa", function (err) {
    log('1.3 err: ', err);
});
//10.669> 1.3 handler: aaa A
//10.831> 1.3 handler: aaa B
//10.834> 1.3 err: null
```
