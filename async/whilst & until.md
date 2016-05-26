+   [async.whilst](#whilst)
+   [async.doWhilst](#dowhilst)
+   [async.until](#until)
+   [async.doUntil](#dountil)

# whilst
whilst(test, fn, callback)

中途出错。出错后立刻调用第三个函数。

```javascript
var count = 0;

async.whilst(
    function () { return count < 5; },
    function (callback) {
        count++;
        setTimeout(function () {
            callback(null, count);
        }, 1000);
    },
    function (err, n) {
        // 5 seconds have passed, n = 5
    }
);
```

# doWhilst
doWhilst(fn, test, callback)

doWhilst交换了fn,test的参数位置，先执行一次循环，再做test判断。 和javascript中do..while语法一致。

```javascript
var count4 = 0;
async.doWhilst(
    function(cb) {
        log('1.4 count: ', count4);
        t.inc(count4++, cb);
    },
    function() { log("1.4 test"); return count4 < 3 },
    function(err,result){ // result没有用
        log('1.4 err: ', err);
        log('1.4 result: ', result);
    }
);
```

# until
until(test, fn, callback)

until与whilst正好相反，当test为false时循环，与true时跳出

# doUntil
doUntil(fn, test, callback)

doUntil与doWhilst正好相反，当test为false时循环，与true时跳出。其它特性一致。
