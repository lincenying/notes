* [async.map](#map)
* [async.mapSeries](#mapseries)
* [async.mapLimit](#maplimit)

```javascript
var arr = [{
    name:'Jack', delay:200
}, {
    name:'Mike', delay: 100
}, {
    name:'Freewind', delay:300
}, {
    name:'Test', delay: 50
}];
```

# map

async.map(coll, iteratee, [callback])

对集合中的每一个元素，执行某个异步操作，得到结果。所有的结果将汇总到最终的callback里

- 并行执行。同时对集合中所有元素进行操作，结果汇总到最终callback里。如果出错，则立刻返回错误以及已经执行完的任务的结果，未执行完的占个空位
- 顺序执行。对集合中的元素一个一个执行操作，结果汇总到最终callback里。如果出错，则立刻返回错误以及已经执行完的结果，未执行的被忽略。

##### 并行

```javascript
async.map(arr, function(item, callback) {
    log('1.1 enter: ' + item.name);
    setTimeout(function() {
        log('1.1 handle: ' + item.name);
        callback(null, item.name + '!!!');
    }, item.delay);
}, function(err,results) {
    log('1.1 err: ', err);
    log('1.1 results: ', results);
});
// => results: [ 'Jack!!!', 'Mike!!!', 'Freewind!!!', 'Test!!!' ]
```

# mapSeries

async.mapSeries(coll, iteratee, [callback])

顺序执行，一个完了才执行下一个。

```javascript
async.mapSeries(arr, function(item, callback) {
    log('1.3 enter: ' + item.name);
    setTimeout(function() {
        log('1.3 handle: ' + item.name);
        callback(null, item.name+'!!!');
    }, item.delay);
}, function(err,results) {
    log('1.3 err: ', err);
    log('1.3 results: ', results);
});
// => results: [ 'Jack!!!', 'Mike!!!', 'Freewind!!!', 'Test!!!' ]
```

# mapLimit

async.mapLimit(coll, limit, iteratee, [callback])

并行执行，同时最多 N 个函数并行，传给最终callback。

```javascript
async.mapLimit(arr,2, function(item, callback) {
    log('1.5 enter: ' + item.name);
    setTimeout(function() {
        log('1.5 handle: ' + item.name);
        if(item.name==='Jack') callback('myerr');
        else callback(null, item.name+'!!!');
    }, item.delay);
}, function(err, results) {
    log('1.5 err: ', err);
    log('1.5 results: ', results);
});
```
