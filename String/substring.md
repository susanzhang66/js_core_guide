## substring 方法

返回位于 String 对象中指定位置的子字符串。

strVariable.substring(start, end)
"String Literal".substring(start, end)

**参数**

**start**
指明子字符串的起始位置，该索引从 0 开始起算。

**end**
指明子字符串的结束位置，该索引从 0 开始起算。

**说明**

substring 方法将返回一个包含从 start 到最后（不包含 end ）的子字符串的字符串。

substring 方法使用` start 和 end 两者中的较小值作为子字符串的起始点。`例如， strvar.substring(0, 3) 和 strvar.substring(3, 0) 将返回相同的子字符串。

`如果 start 或 end 为 NaN 或者负数，那么将其替换为0。`

`子字符串的长度等于 start 和 end 之差的绝对值。`例如，在 strvar.substring(0, 3) 和 strvar.substring(3, 0) 返回的子字符串的的长度是 3。

**示例**

下面的示例演示了 substring 方法的用法。
```javascript
function SubstringDemo(){
   var ss;                         // 声明变量。
   var s = "The rain in Spain falls mainly in the plain..";
   ss = s.substring(12, 17);   // 取子字符串。
   return(ss);                     // 返回子字符串。
}
```