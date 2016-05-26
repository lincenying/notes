+   [async.series](#series)

```javascript
var t = {}
t.inc = function(n, callback, timeout) {
    timeout = timeout || 200;
    setTimeout(function() {
        callback(null, n+1);
    }, timeout);
}
```

# series
async.series(tasks, [callback])

* 串行执行，一个函数数组中的每个函数，每一个函数执行完成之后才能执行下一个函数。
* 中间有函数出错。出错之后的函数不会执行，错误及之前正常执行的函数结果将传给最终的callback。
* 如果某个函数传的数据是undefined, null, {}, []等，它们会原样传给最终callback。
* 以json形式传入tasks。其结果也将以json形式传给最终callback。

```javascript
async.series([
    function(cb) { t.inc(3, cb); },
    function(cb) { t.inc(8, cb); },
    function(cb) { t.inc(2, cb); }
], function(err, results) {
    log('1.1 err: ', err);
    log('1.1 results: ', results);
});

// => results: [ 4, 9, 3 ]
```
