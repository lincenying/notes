+   [async.every](#every)
+   [async.everySeries](#everyseries)
+   [async.everyLimit](#everylimit)
+   [async.some](#every)
+   [async.someSeries](#someseries)
+   [async.someLimit](#somelimit)

```javascript
var arr = [1,2,3,6];
```

# every
async.every(coll, iteratee, [callback])

如果集合里每一个元素都满足条件，则传给最终回调的result为true，否则为false
```javascript
async.every(arr, function(item, callback){
    log('1.1 enter: ',item);
    setTimeout(function(){
        log('1.1 handle: ',item);
        callback(null, item<=10);
    },100);
}, function(result) {
    log('1.1 result: ', result);
});
// 32.233> 1.1 result: true
```

# everySeries
async.everySeries(coll, iteratee, callback)

串行

# everyLimit
async.everyLimit(coll, limit, iteratee, callback)

# some
async.some(arr, iterator(item,callback(test)), callback(result))

并行, 当集合中是否有至少一个元素满足条件时，最终callback得到的值为true，否则为false.

```javascript
async.some(arr, function(item,callback){
    log('1.1 enter: ',item);
    setTimeout(function(){
        log('1.1 handle: ',item);
        callback(null, item<=3);
    },100);
}, function(result) {
    log('1.1 result: ', result);
});
```

# someSeries
async.someSeries(coll, iteratee, callback)

串行

# someLimit
async.someLimit(coll, limit, iteratee, callback)
