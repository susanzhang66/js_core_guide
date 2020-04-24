## Object常用方法总结
Object常用方法总结：
## 1.Object.assign(target,source1,source2,...)
- 该方法主要用于对象的合并，将源对象source的所有可枚举属性合并到目标对象target上,此方法`只拷贝源对象的自身属性`，`不拷贝继承的属性。`
- Object.assign方法实行的是`浅拷贝，而不是深拷贝。`也就是说，如果源对象某个属性的值是对象，那么目标对象拷贝得到的是这个对象的引用。`同名属性会替换。`
- Object.assign只能进行值的复制，`如果要复制的值是一个取值函数，那么将求值后再复制。`
- Object.assign可以用来处理数组，但是`会把数组视为对象。`
```javascript
const target = { x : 0,y : 1};
const source = { x : 1,z : 2 ,fn : {number : 1}};
console.log(Object.assign(target, source));
// target  {x : 1, y : 1, z : 2, fn : {number : 1}}    // 同名属性会被覆盖
target.fn.number = 2;
console.log(source)// source  {x : 1, z : 2, fn : {number : 2}}   // 拷贝为对象引用

function Person(){
  this.name = 1
};
Person.prototype.country = 'china';
var student = new Person();
student.age = 29 ;
const young = {name : 'zhang'};
Object.assign(young,student);
// young {name : 'zhang', age : 29}               // 只能拷贝自身的属性，不能拷贝prototype

Object.assign([1, 2, 3], [4, 5])                      // 把数组当作对象来处理
// [4, 5, 3]
```
## 2.Object.create(prototype,[propertiesObject])   实现类式继承。
 使用指定的原型对象及其属性去创建一个新的对象
**参数**：
**proto**
- 新创建对象的原型对象。
**propertiesObject**
- 可选。如果没有指定为 undefined，则是要添加到新创建对象的不可枚举（默认）属性（即其自身定义的属性，而不是其原型链上的枚举属性）对象的属性描述符以及相应的属性名称。这些属性对应Object.defineProperties()的第二个参数。

```javascript
var parent = { x : 1,y : 1}
var child = Object.create(parent,{
  z : {                           // z会成为创建对象的属性
    writable:true,
    configurable:true,
    value: "newAdd"
  }
});
console.log(child) //{z:"newAdd"}
console.log(child.x) //1

//类式继承。
function MyClass() {
     SuperClass.call(this);
     OtherSuperClass.call(this);
}

// 继承一个类
MyClass.prototype = Object.create(SuperClass.prototype);
// 混合其它
Object.assign(MyClass.prototype, OtherSuperClass.prototype);
// 重新指定constructor
MyClass.prototype.constructor = MyClass;

MyClass.prototype.myMethod = function() {
     // do a thing
};
```

## 3.Object.defineProperties(obj,props)
直接在一个对象上定义新的属性或修改现有属性，并返回该对象。
```javascript
var obj = {};
Object.defineProperties(obj, {
  'property1': {
    value: true,
    writable: true
  },
  'property2': {
    value: 'Hello',
    writable: false
  }
});
console.log(obj)   // {property1: true, property2: "Hello"}
```
## 4.Object.defineProperty(obj,prop,descriptor)
在一个对象上定义一个新属性，或者修改一个对象的现有属性， 并返回这个对象。
```javascript
Object.defineProperty(Object, 'is', {
  value: function(x, y) {
           if (x === y) {
          // 针对+0 不等于 -0的情况
              return x !== 0 || 1 / x === 1 / y;
          }
          // 针对NaN的情况
          return x !== x && y !== y;
  },
  configurable: true,
  enumerable: false,
  writable: true
});
```
// 注意不能同时设置(writable，value) 和 get，set方法，否则浏览器会报错 ： Invalid property descriptor. Cannot both specify accessors and a value or writable attribute

## 5.Object.keys(obj)
返回一个由一个给定对象的自身`可枚举属性组成的数组`，数组中属性名的排列顺序和使用 for...in 循环遍历该对象时返回的顺序一致 （两者的`主要区别是 一个 for-in 循环还会枚举其原型链上的属性）。`

```javascript
var arr = ["a", "b", "c"];
console.log(Object.keys(arr));
// ['0', '1', '2']

/* Object 对象 */
var obj = { foo: "bar", baz: 42 },
keys = Object.keys(obj);
console.log(keys);
// ["foo","baz"]
```
## 6.Object.values( obj )
方法返回一个给定对象自己的所有可枚举属性值的`数组`，值的顺序与使用for...in循环的顺序相同 ( 区别在于 for-in 循环枚举原型链中的属性 )。
`Object.values会过滤属性名为 Symbol 值的属性。`
```javascript
var an_obj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.values(an_obj)); // ['b', 'c', 'a']

var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.values(obj)); // ['a', 'b', 'c']
```
## 7.Object.entries()
返回一个给定对象自身可枚举属性的`键值对数组`，其排列与使用 for...in 循环遍历该对象时返回的顺序一致（区别在于 for-in 循环也枚举原型链中的属性）。
```javascript
const obj = { foo: 'bar', baz: 42 };
console.log(Object.entries(obj)); // [ ['foo', 'bar'], ['baz', 42] ]

const simuArray = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.entries(simuArray)); // [ ['0', 'a'], ['1', 'b'], ['2', 'c'] ]
```

## 8.hasOwnProperty()
- 判断对象自身属性中是否具有指定的属性。
  
> obj.hasOwnProperty('name')

## 9.Object.getOwnPropertyNames()
返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性但不包括Symbol值作为名称的属性）组成的`数组。`
```javascript
var obj = { 0: "a", 1: "b", 2: "c"};
Object.getOwnPropertyNames(obj).forEach(function(val) {
  console.log(val);
});
//0,1,2
var obj = {
  x : 1,
  y : 2
}
Object.defineProperty(obj,'z',{
  enumerable : false
})
console.log(Object.getOwnPropertyNames(obj))  // ["x", "y", "z"] 包含不可枚举属性 。
console.log(Object.keys(obj))                 // ["x", "y"]      只包含可枚举属性 。
```
## 10.isPrototypeOf()
判断一个对象是否存在于另一个对象的原型链上。

## 11.Object.setPrototypeOf(obj,prototype)
设置对象的原型对象

## 12.Object.is()
判断两个值是否相同。

**如果下列任何一项成立，则两个值相同：**
  - 两个值都是 undefined
  - 两个值都是 null
  - 两个值都是 true 或者都是 false
  - 两个值是由相同个数的字符按照相同的顺序组成的字符串
  - 两个值指向同一个对象
  - 两个值都是数字并且
  - 都是正零 +0
  - 都是负零 -0
  - 都是 NaN
  - 都是除零和 NaN 外的其它同一个数字

```javascript
Object.is('foo', 'foo');     // true
Object.is(window, window);   // true

Object.is('foo', 'bar');     // false
Object.is([], []);           // false

var test = { a: 1 };
Object.is(test, test);       // true

Object.is(null, null);       // true

// 特例
Object.is(0, -0);            // false
Object.is(-0, -0);           // true
Object.is(NaN, 0/0);         // true
```
## 13.Object.freeze()
冻结一个对象，冻结指的是不能向这个对象添加新的属性，不能修改其已有属性的值，不能删除已有属性，以及不能修改该对象已有属性的可枚举性、可配置性、可写性。也就是说，这个对象永远是不可变的。该方法返回被冻结的对象。

var obj = {
  prop: function() {},
  foo: 'bar'
};

// 新的属性会被添加, 已存在的属性可能
// 会被修改或移除
obj.foo = 'baz';
obj.lumpy = 'woof';
delete obj.prop;

// 作为参数传递的对象与返回的对象都被冻结
// 所以不必保存返回的对象（因为两个对象全等）
var o = Object.freeze(obj);

o === obj; // true
Object.isFrozen(obj); // === true

// 现在任何改变都会失效
obj.foo = 'quux'; // 静默地不做任何事
// 静默地不添加此属性
obj.quaxxor = 'the friendly duck';
console.log(obj)

## 14.Object.isFrozen()
判断一个对象是否被冻结 .

## 15.Object.preventExtensions()
对象不能再添加新的属性。可修改，删除现有属性，不能添加新属性。
```javascript
var obj = {
  name :'lilei',
  age : 30 ,
  sex : 'male'
}

obj = Object.preventExtensions(obj);
console.log(obj);    // {name: "lilei", age: 30, sex: "male"}
obj.name = 'haha';
console.log(obj)     // {name: "haha", age: 30, sex: "male"}
delete obj.sex ;
console.log(obj);    // {name: "haha", age: 30}
obj.address  = 'china';
console.log(obj)     // {name: "haha", age: 30}

```