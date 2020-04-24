**定义和用法**  ie9+
forEach() 方法用于调用数组的每个元素，并将元素传递给回调函数。


> array.forEach(function(currentValue, index, arr), thisValue)

- currentValue	必需。当前元素
- index	可选。当前元素的索引值。
- arr	可选。当前元素所属的数组对象。

```javascript
var num = [1,2,3,4,5];
num.forEach(function(item, index){
  console.log(item);
})
```

**注意**: forEach() 对于空数组是不会执行回调函数的。