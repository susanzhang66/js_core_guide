<!--
 * @Author: your name
 * @Date: 2020-04-24 14:31:52
 * @LastEditTime: 2020-04-24 14:35:02
 * @LastEditors: your name
 * @Description: In User Settings Edit
 * @FilePath: /vue/Users/rainbow/Documents/工作/前端/learn/JS参考手册/Array/every9+.md
 -->
**定义和用法** 9+
every() 方法用于检测数组所有元素是否都符合指定条件（通过函数提供）。

every() 方法使用指定函数检测数组中的所有元素：
- 如果数组中检测到有一个元素不满足，则整个表达式返回 false ，且剩余的元素不会再进行检测。
- 如果所有元素都满足条件，则返回 true。

**注意**： every() 不会对空数组进行检测。
**注意**： every() 不会改变原始数组。

> array.every(function(currentValue,index,arr), thisValue)

- currentValue	必须。当前元素的值
- index	可选。当前元素的索引值
- arr	可选。当前元素属于的数组对象

```javascript
var ages = [32, 33, 12, 40];

function checkAdult(age) {
    return age >= document.getElementById("ageToCheck").value;
}

function myFunction() {
    document.getElementById("demo").innerHTML = ages.every(checkAdult);
}
```