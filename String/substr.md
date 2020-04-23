## substr 方法

返回一个从指定位置开始的指定长度的子字符串。

stringvar.substr(start [, length ])

**参数**

**stringvar**
必选项。要提取子字符串的字符串文字或 String 对象。

**start**
必选项。所需的子字符串的起始位置。字符串中的第一个字符的索引为 0。 如果为负数，则从倒数位置算。

**length**
可选项。在返回的子字符串中应包括的字符个数。

**说明**

如果 `length 为 0 或负数，将返回一个空字符串。`如果没有指定该参数，则子字符串将延续到 stringvar 的最后。

示例

下面的示例演示了substr 方法的用法。
```javascript
function SubstrDemo(){
   var s, ss;                // 声明变量。
   var s = "The rain in Spain falls mainly in the plain.";
   ss = s.substr(12, 5);  // 获取子字符串。
   return(ss);               // 返回 "Spain"。
}
```
