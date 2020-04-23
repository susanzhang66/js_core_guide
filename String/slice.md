<!--
 * @Author: your name
 * @Date: 2020-04-23 16:30:20
 * @LastEditTime: 2020-04-23 16:35:44
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /vue/Users/rainbow/Documents/工作/前端/learn/JS参考手册/String/slice.md
 -->
## slice 方法 (String)

返回字符串的片段。

stringObj.slice(start, [end])

**参数**

**stringObj**
必选项。是一个 String 对象或文字。

**start**
必选项。下标以 0 开始的 stringObj 指定部分起始索引。

**end**
可选项。下标以 0 起始的 stringObj 的指定部分结束索引。

说明

slice 方法返回一个包含 stringObj 的指定部分的 String 对象。

slice 方法一直复制到 end 所指定的元素，但是不包括该元素。`如果 start 为负，将它作为 length + start处理，此处 length 为数组的长度。如果 end 为负，就将它作为 length + end 处理，`此处 length 为数组的长度。如果省略 end ，那么 slice 方法将一直复制到 arrayObj 的结尾。`如果 end 出现在 start 之前，不复制任何元素到新数组中。即返回空数组`

示例

在下面的示例中，slice 方法的两种用法将返回相同的结果。第二个示例中的 -1 指向 str1 中的最后一个字符，并作为提取操作的结束位置。

str1.slice(0)
str2.slice(0,-1)

str3.slice(4,3) // "";



**比较substring**(); 
1. 参数不可以为负数和NaN，如果是，变成0。
2. start可以比end大，返回的是绝对值，跟end>start是一样的。
**slice**(): 参数可以是负数

substr(start, length):start可以是负数，即倒数。 length是NaN或负数则返回空字符串。