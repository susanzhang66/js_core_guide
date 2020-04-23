<!--
 * @Author: your name
 * @Date: 2020-04-23 15:35:07
 * @LastEditTime: 2020-04-23 15:37:39
 * @LastEditors: your name
 * @Description: In User Settings Edit
 * @FilePath: /vue/Users/rainbow/Documents/工作/前端/learn/JS参考手册/String/replace.md
 -->

## stringObj.replace(rgExp, replaceText)

返回根据正则表达式进行文字替换后的字符串的复制。

>stringObj.replace(rgExp, replaceText)

**参数**

**stringObj**
必选项。要执行该替换的 String 对象或字符串文字。该字符串不会被 replace 方法修改。

**rgExp**
必选项。为包含正则表达式模式或可用标志的正则表达式对象。也可以是 String 对象或文字。如果 rgExp 不是正则表达式对象，它将被转换为字符串，并进行精确的查找；不要尝试将字符串转化为正则表达式。

**replaceText**
必选项。是一个String 对象或字符串文字，对于stringObj 中每个匹配 rgExp 中的位置都用该对象所包含的文字加以替换。在 Jscript 5.5 或更新版本中，replaceText 参数也可以是返回替换文本的函数。


**说明**
字符串 stringObject 的 replace() 方法执行的是查找并替换的操作。它将在 stringObject 中查找与 regexp 相匹配的子字符串，然后用 replacement 来替换这些子串。如果 regexp 具有全局标志 g，那么 replace() 方法将替换所有匹配的子串。否则，它只替换第一个匹配子串。

replacement 可以是字符串，也可以是函数。如果它是字符串，那么每个匹配都将由字符串替换。但是 replacement 中的 $ 字符具有特定的含义。如下表所示，它说明从模式匹配得到的字符串将用于替换。

> 
- $1、$2、...、$99	与 regexp 中的第 1 到第 99 个子表达式相匹配的文本。
- $&	与 regexp 相匹配的子串。
- $`	位于匹配子串左侧的文本。
- $'	位于匹配子串右侧的文本。
- \$$	直接量符号。


```javascript
text = "javascript Tutorial";
text.replace(/javascript/i, "JavaScript");

name = "Doe, John";
name.replace(/(\w+)\s*, \s*(\w+)/, "$2 $1");

name = '"a", "b"';
name.replace(/"([^"]*)"/g, "'$1'");

name = 'aaa bbb ccc';
uw=name.replace(/\b\w+\b/g, function(word){
  return word.substring(0,1).toUpperCase()+word.substring(1);}
);

```