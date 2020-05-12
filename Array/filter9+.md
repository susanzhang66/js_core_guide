<!--
 * @Author: your name
 * @Date: 2020-04-24 14:05:05
 * @LastEditTime: 2020-04-24 14:05:06
 * @LastEditors: your name
 * @Description: In User Settings Edit
 * @FilePath: /vue/Users/rainbow/Documents/工作/前端/learn/JS参考手册/Array/filter.md
 -->
**定义和用法**   ie9+
filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

> array.filter(function(currentValue,index,arr), thisValue)

currentValue	必须。当前元素的值
index	可选。当前元素的索引值
arr	可选。当前元素属于的数组对象

返回值：返回数组，包含了符合条件的所有元素。如果没有符合条件的元素则返回空数组。

注意： filter() 不会对空数组进行检测。
注意： filter() 不会改变原始数组。


```javascript
var ages = [32, 33, 16, 40];

function checkAdult(age) {
    return age >= 18;
}

function myFunction() {
    document.getElementById("demo").innerHTML = ages.filter(checkAdult);
}
```