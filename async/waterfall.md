+   [async.waterfall](#waterfall)

# waterfall

* 按顺序依次执行一组函数, 每个函数产生的值，都将传给下一个。
* 所有函数正常执行，每个函数的结果都将变为下一个函数的参数
* 中途有函数出错，其err直接传给最终callback，结果被丢弃，后面的函数不再执行。
* 以json形式传入tasks，将不会被执行

```javascript
async.waterfall([
    (cb) => cb(null, 3),
    (n, cb) => {
        console.log(n); // => 3
        cb(null, 4);
    },
    (n, cb) => {
        console.log(n); // => 4
        cb(null, 5);
    }
], (err, result) => {
    console.log(err);
    console.log(result);
});
// => result: 5
```
