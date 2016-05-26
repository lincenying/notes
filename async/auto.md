+   [async.auto](#auto)

# auto
async.auto(tasks, [callback])

auto用来处理有依赖关系的多个任务的执行
如果中途出错，则会把错误交给最终callback，执行完任务的传给最终callback。未执行完成的函数值被忽略

```javascript
async.auto({
    getData: function (callback) {
        setTimeout(function(){
            console.log('1.1: got data');
             callback(null, 'mydata');
        }, 300);
    },
    makeFolder: function (callback) {
        setTimeout(function(){
            console.log('1.1: made folder');
            callback(null, 'myfolder');
        }, 200);
    },
    writeFile: ['getData', 'makeFolder', function(callback) {
        setTimeout(function(){
            console.log('1.1: wrote file');
            callback(null, 'myfile');
        }, 300);
    }],
    emailFiles: ['writeFile', function(callback, results) {
        log('1.1: emailed file: ', results.writeFile);
        callback(null, results.writeFile);
    }]
}, function(err, results) {
    log('1.1: err: ', err);
    log('1.1: results: ', results);
});
```
