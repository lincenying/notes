+   [async.compose](#compose)

# compose
创建一个包括一组异步函数的函数集合，每个函数会消费上一次函数的返回值。

```javascript
function fn1(n,callback){
    log('1.1.f enter: ',n);
    setTimeout(function () {
        callback(null, n + 1);
    }, 10);
}
function fn2(n, callback) {
    log('1.1.g enter: ',n);
    setTimeout(function () {
        callback(null, n * 2);
    }, 10);
}
function fn3(n, callback) {
    log('1.1.h enter: ',n);
    setTimeout(function () {
        callback(null, n - 10);
    }, 10);
}
var fn = async.compose(fn1, fn2, fn3);
fn(4, function(err,result){
    log('1.1 err: ', err);
    log('1.1 result: ', result);
});
//05.307> 1.1.h enter: 4
//05.329> 1.1.g enter: -6
//05.341> 1.1.f enter: -12
//05.361> 1.1 err: null
//05.362> 1.1 result: -11
```
