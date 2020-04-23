<!--
 * @Author: your name
 * @Date: 2020-04-23 14:37:23
 * @LastEditTime: 2020-04-23 15:28:56
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /vue/Users/rainbow/Documents/工作/前端/learn/JS参考手册/String/match.md
 -->
##String对象
match 方法

使用正则表达式模式对字符串执行查找，并将包含查找的结果作为数组返回。

stringObj.match(rgExp)

##参数

**stringObj**
必选项。对其进行查找的 String 对象或字符串文字。

**rgExp**
必选项。为包含正则表达式模式和可用标志的正则表达式对象。也可以是包含正则表达式模式和可用标志的变量名或字符串文字。

**下面的示例演示了match方法的用法：**
```javascript
function MatchDemo(){
   var r, re;         // 声明变量。
   var s = "The rain in Spain falls mainly in the plain";
   re = /ain/i;    // 创建正则表达式模式。
   r = s.match(re);   // 尝试匹配搜索字符串。
   return(r);         // 返回第一次出现 "ain" 的地方。
}
// 本示例说明带 g 标志设置的 match 方法的用法。

function MatchDemo(){
   var r, re;         // 声明变量。
   var s = "The rain in Spain falls mainly in the plain";
   re = /ain/ig;      // 创建正则表达式模式。
   r = s.match(re);   // 尝试去匹配搜索字符串。
   return(r);         // 返回的数组包含了所有 "ain" 
                      // 出现的四个匹配。
}
```
**下面几行代码演示了字符串文字的match 方法的用法。**
```javascript
var r, re = "Spain";
r = "The rain in Spain".replace(re, "Canada");
```