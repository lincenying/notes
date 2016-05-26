# nextTick
async.nextTick(callback, [args...])

```javascript
var calls = [];
async.nextTick(function() {
    calls.push('two');
});
async.nextTick(function() {
    log('1.1',calls);
});
calls.push('one');
log('1.2',calls);
async.nextTick(function() {
    log('1.3',calls);
});
//09.838> 1.2[ 'one' ]
//09.842> 1.1[ 'one', 'two' ]
//09.843> 1.3[ 'one', 'two' ]
```
