+   [async.filter](#filter)
+   [async.filterSeries](#filterseries)
+   [async.filterLimit](#filterlimit)
+   [async.reject](#reject)

```javascript
var arr = [1,2,3,6];
```

# filter
async.filter(coll, iteratee, [callback])

并行执行，对arr进行筛选。

```javascript
async.filter(arr, function(item, callback) {
    log('1.1 enter: ' + item);
    setTimeout(function() {
        log('1.1 test: ' + item);
        callback(null, item>=3);
    }, 200);
}, function(results) {
    log('1.1 results: ', results);
});
// ==> results: [ 3, 4, 5 ]
```

# filterSeries
async.filterSeries(coll, iteratee, [callback])

串行执行，对arr进行筛选。

```javascript
async.filterSeries(arr, function(item, callback) {
    log('1.3 enter: ' + item);
    setTimeout(function() {
        log('1.3 handle: ' + item);
        callback(null, item>=3);
    }, 200);
}, function(results) {
    log('1.3 results: ', results);
});
// => results: [ 3, 4, 5 ]
```

# filterLimit
async.filterLimit(coll, limit, iteratee, [callback])

# reject
* async.reject(coll, iteratee, [callback])
* async.rejectSeries(coll, iteratee, [callback])
* async.rejectLimit(coll, limit, iteratee, [callback])

reject跟filter正好相反，当测试为true时，抛弃之

```javascript
async.reject(arr, function(item, callback) {
    log('1.4 enter: ' + item);
    setTimeout(function() {
        log('1.4 test: ' + item);
        callback(null, item>=3);
    }, 200);
}, function(results) {
    log('1.4 results: ', results);
});
// => results: [ 1, 2 ]

async.rejectSeries(arr, function(item, callback) {
    log('1.5 enter: ' + item);
    setTimeout(function() {
        log('1.5 handle: ' + item);
        callback(null, item>=3);
    }, 200);
}, function(results) {
    log('1.5 results: ', results);
});
// => results: [ 1, 2 ]
```
