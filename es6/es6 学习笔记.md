###### let与const 关键字

可以把let看成var，只是它定义的变量被限定在了特定范围内才能使用，而离开这个范围则无效。
const则很直观，用来定义常量，即无法被更改值的变量。

###### 模块化写法

```javascript
export function func() {

}
//==>
exports.func = function(){

}
```

对应import方法:
```javascript
import * as GoTop from "./module/go-top";
//或者
import { func } from "./module/go-top";
//注意: func要和export的函数名一致
```

```javascript
export default {

}
//==>
module.exports = {

}
```

###### 加载模块

```javascript
import api from '../api';
//==>
var api = require('../api');
```

* 通过 import * as 就完成了模块整体的导入
* 通过指令 module 也可以达到整体的输入

###### 对象函数
```javascript
var Obj = {
    func1(e) {

    },
    func2(e) {

    }
}
//==>
var Obj = {
    func1: function(e) {

    },
    func2: function(e) {

    }
}
```

###### 箭头函数

```javascript
this.$on('isOpenEvent', (e)=> {
    //单条语句时, 不需要花挂号包裹
});
//==>
this.$on('isOpenEvent', function (e) {

});
```

```javascript
const arr = [1,2,3];
arr.map(item => item + 1);
//==>
var arr = [1,2,3];
arr.map(function(item){
    return item + 1;
});
```

###### 对象引用

```javascript
import alert from './Alert.vue';
var Obj = {
    alert
};
//==>
var alert = require('./Alert.vue');
var Obj = {
    alert: alert
};
```javascript

###### 字符串模板

```javascript
var num=Math.random();
console.log(`your num is ${num}`);
//==>
var num = Math.random();
console.log("your num is " + num);
```

###### 自动解析数组

```javascript
[name,,age]=['wayou','male','secrect'];
//==>
var arr = ['wayou', 'male', 'secrect'];
name = arr[0];
age = arr[2];
```

###### 参数默认值, 不定参数, 拓展参数

参数默认值
```javascript
function func(name='dude'){
	console.log(`Hello ${name}`);
}
//==>
function func() {
	var name = arguments.length <= 0 || arguments[0] === undefined ? 'dude' : arguments[0];
	console.log('Hello ' + name);
}
```

不定参数
```javascript
function func(...x){
    console.log(x);
}
//==>
function func() {
    for (var _len = arguments.length, x = Array(_len), _key = 0; _key < _len; _key++) {
        x[_key] = arguments[_key];
    }
    console.log(x);
}
```

拓展参数
```javascript
var people=['Wayou','John','Sherlock'];
function func(people1,people2,people3){
	console.log(`Hello ${people1},${people2},${people3}`);
}

func(...people);
//==>
func.apply(null,people);
```
