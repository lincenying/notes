+   [async.parallel](#parallel)
+   [async.parallelLimit](#parallellimit)

# parallel
async.parallel(tasks, [callback])

* 并行执行多个函数，每个函数的值将按函数声明的先后顺序汇成一个数组，传给最终callback。
* 如果中途有个函数出错，则将该err和已经完成的函数值汇成一个数组，传给最终的callback。还没有执行完的函数的值将被忽略，但要在最终数组中占个位置
* 以json形式传入tasks，最终results也为json

```javascript
async.parallel([
    (cb) => {
        setTimeout(() => {
            cb(null, 100);
        }, 100);
    },
    (cb) => {
        setTimeout(() => {
            cb(null, 200);
        }, 200);
    },
    (cb) => {
        setTimeout(() => {
            cb(null, 300);
        }, 300);
    }
], function (err, results) {
    log('1.1 err: ', err);
    log('1.1 results: ', results);
});
```

# parallelLimit
async.parallelLimit(tasks, limit, [callback])

并行执行，同时最多 N 个函数并行，传给最终callback。

```javascript
async.parallel({
    a(cb) => {
        setTimeout(() => {
            cb(null, 100);
        }, 100);
    },
    b(cb) => {
        setTimeout(() => {
            cb(null, 200);
        }, 200);
    },
    c(cb) => {
        setTimeout(() => {
            cb(null, 300);
        }, 300);
    }
}, 2, function (err, results) {
    log('1.1 err: ', err);
    log('1.1 results: ', results);
});
```
