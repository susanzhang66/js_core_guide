<!--
 * @Author: your name
 * @Date: 2020-04-26 13:20:22
 * @LastEditTime: 2020-04-26 13:22:52
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /vue/Users/rainbow/Documents/工作/前端/learn/JS参考手册/String/includes.md
 -->
**定义和用法**
## includes() 方法用于判断字符串是否包含指定的子字符串。

如果找到匹配的字符串则返回 true，否则返回 false。

> string.includes(searchvalue, start)

**注意**： includes() 方法区分大小写。

```javascript
var str = "Hello world, welcome to the Runoob。";
var n = str.includes("world");
// 用indexOf实现。
var string = 'food';
var substring = 'foo';
console.log(string.indexOf(substring) > -1);
```