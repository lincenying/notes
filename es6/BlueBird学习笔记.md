* Promise.all 会等所有 Promise 执行完毕后，把结果放在数组里
* Promise.reduce 按顺序执行
* Promise.mapSeries 方法，这个方法和 Promise.map 类似，只不过是顺序执行的
* Promise.each 方法，和 Promise.mapSeries 方法类似，都是顺序执行，区别是，返回的数组不是所有 Promise 的结果，而是传入 Promise.each 方法的原始数据数组

```javascript
var Promise = require('bluebird');
var p1 = new Promise((resolve, reject) => {
    setTimeout(()=>{
        resolve(1000)
    }, 1000);
});
var p2 = new Promise((resolve, reject) => {
    setTimeout(()=>{
        resolve(2000)
    }, 2000);
});
var p3 = new Promise((resolve, reject) => {
    setTimeout(()=>{
        resolve(3000)
    }, 3000);
});

new Promise((resolve, reject) => {
    setTimeout(()=>{
        resolve(2000)
    }, 1000);
}).then((value) => {
    console.log(value); // 2000
    return new Promise((resolve, reject) => {
        setTimeout(()=>{
            resolve(3000)
        }, value);
    })
}).then((value) => {
    console.log(value) // 3000
})
```

# all
无执行顺序
```javascript
Promise.all([p1, p2]).then(function(value) {
    console.log(value); // [ 1000, 2000 ]
});
```

# props
```javascript
Promise.props({
    pictures: p1,
    comments: p2
}).then(function(result) {
    console.log(result); // { pictures: 1000, comments: 2000 }
});
```

# some
```javascript
Promise.some([
    p1, p2, p3
], 2).spread(function(first, second) {
    console.log(first, second);
});
```
```javascript
function makePromise(name, delay) {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(name);
        }, delay);
    });
}
var data = [2000, 1, 1000];
```
# reduce

顺序执行
```javascript
Promise.reduce(data, (total, item, index) => {
    return makePromise(index, item).then(res => {
        return total + res;
    });
}, 0).then(res => {
    console.log(res);
});
```

# mapSeries
```javascript
Promise.mapSeries(data, (item, index) => {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(index);
        }, item);
    });
}, 0).get(1).then(res => {
    console.log(res);
});
```
