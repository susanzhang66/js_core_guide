

**直接量**
> /pattern/attributes

**创建 RegExp 对象的语法**

> new RegExp(pattern, attributes);


**返回值**
一个新的 RegExp 对象，具有指定的模式和标志。如果参数 pattern 是正则表达式而不是字符串，那么 RegExp() 构造函数将用与指定的 RegExp 相同的模式和标志创建一个新的 RegExp 对象。

`如果不用 new 运算符，`而将 RegExp() 作为函数调用，那么它的行为与用 new 运算符调用时一样，`只是当 pattern 是正则表达式时，它只返回 pattern，而不再创建一个新的 RegExp 对象。`


**属性：**
global	RegExp 对象是否具有标志 g。	
ignoreCase	RegExp 对象是否具有标志 i。	
lastIndex	一个整数，标示开始下一次匹配的字符位置。	
multiline	RegExp 对象是否具有标志 m。	
source	正则表达式的源文本。

**方法：**
- compile	编译正则表达式。	compile() 方法也可用于改变和重新编译正则表达式。
- exec	检索字符串中指定的值。返回找到的值，并确定其位置。	
  - RegExpObject.exec(string)
  - 返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null。
  - 不带g的情况，第一个参数是匹配的字符串，第二个是子表达式，依次类推。返回的数组与调用方法 String.match() 返回的数组是相同的。
  - `重要事项：`如果在一个字符串中完成了一次模式匹配之后要开始检索新的字符串，就必须手动地把 lastIndex 属性重置为 0。
 ```javascript
 //这个是带g的情况。
  var str = "Visit W3School"; 
  var patt = new RegExp("W3School","g");
  var result;

  while ((result = patt.exec(str)) != null)  {
    document.write(result);
    document.write("<br />");
    document.write(patt.lastIndex);
  }
 ```
- test	检索字符串中指定的值。返回 true 或 false。
  > RegExpObject.test(string)
  **返回值**
    如果字符串 string 中含有与 RegExpObject 匹配的文本，则返回 true，否则返回 false。

  **说明**
  调用 RegExp 对象 r 的 test() 方法，并为它传递字符串 s，与这个表示式是等价的：(r.exec(s) != null)。



  ## 对比字符串的 支持正则的方法
- `search()`	检索与正则表达式相匹配的值。	
    - `stringObject.search(regexp)`
    - 返回值：stringObject 中第一个与 regexp 相匹配的子串的起始位置。没找到返回 -1。
    - search() 方法不执行全局匹配，它将忽略标志 g。
- `match()`	找到一个或多个正则表达式的匹配。	
    - `stringObject.match(searchvalue)` : searchvalue:要匹配的字符串
    - `stringObject.match(regexp)`  regexp：正则表达式
    - 返回值
      存放匹配结果的数组。该数组的内容依赖于 regexp 是否具有全局标志 g。
  ```javascript
  var str="1 plus 2 equal 3"
   str.match(/\d+/g)
  ```
- `replace()`	替换与正则表达式匹配的子串。-- https://www.w3school.com.cn/jsref/jsref_replace.asp
  `stringObject.replace(regexp/substr,replacement)`
  replacement: 字符串值，或者一个替换文本或生成替换文本的函数。
  返回值：
  一个新的字符串，是用 replacement 替换了 regexp 的第一次匹配或所有匹配之后得到的。

  ```javascript
    name = "Doe, John";
    name.replace(/(\w+)\s*, \s*(\w+)/, "$2 $1");


    name = 'aaa bbb ccc';
    uw=name.replace(/\b\w+\b/g, function(word){
      return word.substring(0,1).toUpperCase()+word.substring(1);}
    );
  ```
- `split`	把字符串分割为字符串数组。