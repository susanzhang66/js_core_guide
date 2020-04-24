**定义和用法**
isArray() 方法用于判断一个对象是否为数组。

如果对象是数组返回 true，否则返回 false。

> Array.isArray(obj)


```javascript
function myFunction() {
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var x = document.getElementById("demo");
    x.innerHTML = Array.isArray(fruits);
}

```