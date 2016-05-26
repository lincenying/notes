+   [async.sortBy](#sortby)

# sortBy
async.sortBy(coll, iteratee, [callback])

对集合内的元素进行排序，依据每个元素进行某异步操作后产生的值，从小到大排序。

```javascript
async.sortBy(arr, function(item, callback) {
    setTimeout(function() {
        callback(null,item);
    }, 200);
}, function(err,results) {
    log('1.1 err: ', err);
    log('1.1 results: ', results);
});

// => results: [ 1, 3, 6 ]
```
