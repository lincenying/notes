#### Number.isFinite()用来检查一个数值是否非无穷（infinity）。
#### Number.isNaN()用来检查一个值是否为NaN。
#### Number.isInteger()用来判断一个值是否为整数。

#### Math.trunc()：去除一个数的小数部分，返回整数部分。对于空值和无法截取整数的值，返回NaN。

#### Math.sign()：判断一个数到底是正数、负数、还是零。
返回五种值：参数为正数，返回+1；参数为负数，返回-1；参数为0，返回0；参数为-0，返回-0;其他值，返回NaN。

#### Math.cbrt：计算一个数的立方根。

#### Math.fround：返回一个数的单精度浮点数形式

#### Math.hypot：返回所有参数的平方和的平方根


#### Array.from方法用于将两类对象转为真正的数组：类似数组的对象（array-like object）和可遍历（iterable）的对象

#### Array.of方法用于将一组值，转换为数组。

#### Array.find方法，用于找出第一个符合条件的数组成员。如果没有符合条件的成员，则返回undefined。

#### Array.findIndex方法，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1。

#### Array.fill()使用给定值，填充一个数组

#### entries(), keys(), values()
用于遍历数组。它们都返回一个遍历器，可以用for...of循环进行遍历，唯一的区别是keys()是对键名的遍历、values()是对键值的遍历，entries()是对键值对的遍历。

#### Object.assign方法用来将源对象（source）的所有可枚举属性，复制到目标对象（target）。


#### 匿名函数:

```javascript
hello(){}
// 等同于
hello: function(){}
```

#### 默认参数:
```javascript
function test(name='LCY') {
    console.log(name);
}
```

#### rest参数（形式为“...变量名”）
```javascript
function add(...values) {
    console.log(values);
}
```

#### 扩展运算符（spread）是三个点（...）

#### 箭头函数是使用=>语法的函数简写形式。
```javascript
[1,2,3,4].forEach(v => console.log(v));
```

#### 函数绑定运算符是并排的两个双引号（::），双引号左边是一个对象，右边是一个函数。
