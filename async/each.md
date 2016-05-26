+   [async.each](#each)
+   [async.eachSeries](#eachseries)
+   [async.eachLimit](#eachlimit)
+   [async.forEachOf](#foreachof)
+   [async.forEachOfSeries](#foreachofseries)
+   [async.forEachOfLimit](#foreachoflimit)

```javascript
var arr = [{
    name: 'Jack',
    delay: 200
}, {
    name: 'Mike',
    delay: 100
}, {
    name: 'Freewind',
    delay: 300
}];
```

# each
async.each(coll, iterate, [callback])

所有操作并发执行，且全部未出错，最终得到的err为undefined。注意最终callback只有一个参数err。
如果中途出错，则出错后马上调用最终的callback。其它未执行完的任务继续执行

```javascript
async.each(arr, (item, callback) => {
    setTimeout(() => {
        console.log(item.name);
        callback(null, item.name);
    }, item.delay);
}, (err) => console.log(err));
```

# eachSeries
async.eachSeries(coll, 迭代, [callback])

与each相似，但不是并行执行。而是一个个按顺序执行
如果中途出错，则马上把错误传给最终的callback，还未执行的不再执行

```javascript
async.eachSeries(arr, (item, callback) => {
    setTimeout(() => {
        console.log(item.name);
        callback(null, item.name);
    }, item.delay);
}, (err) => console.log(err));
```

# eachLimit
async.eachLimit(coll, limit, iterate, [callback])

分批执行，第二个参数是每一批的个数。每一批内并行执行，但批与批之间按顺序执行
如果中途出错，错误将马上传给最终的callback。同一批中的未执行完的任务还将继续执行，但下一批及以后的不再执行。

```javascript
async.eachLimit(arr, 2, (item, callback) => {
    setTimeout(() => {
        console.log(item.name);
        callback(null, item.name);
    }, item.delay);
}, (err) => {
    console.log(err);
});
```

# forEachOf
async.forEachOf(coll, iteratee, [callback])

```javascript
var obj = {dev: "/dev.json", test: "/test.json", prod: "/prod.json"};
var configs = {};

async.forEachOf(obj, function (value, key, callback) {
    setTimeout(() => {
        configs[key] = "http://www.baidu.com"+value;
        callback();
    }, 1000);
}, function (err) {
    if (err) console.error(err.message);
    console.log(configs);
});
```

# forEachOfSeries
async.forEachOfSeries(coll, iteratee, [callback])

# forEachOfLimit
async.forEachOfLimit(coll, limit, iteratee, [callback])
