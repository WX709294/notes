# javascript 判断数据类型的几种方法

### javascript 判断数据类型的几种方法
一、typeof 直接返回数据类型字段，但是无法判断数组、null、对象

| typeof 1 | typeof NaN |  typeof "1" | typeof true |  typeof undefined | typeof null | typeof []   | typeof {}  |
|  ----    | ----       |  ----       | ----        |  ----             | ----        |  ----       |  ----      |
| number   | number     |  string     | boolean     | undefined         | object      |  object     |  object    |

二、instanceof 判断某个实例是不是属于原型

```
  // 构造函数
  function Fruit(name, color) {
      this.name = name;
      this.color = color;
  }
  var apple = new Fruit("apple", "red");

  // (apple != null)
  apple instanceof Object  // true
  apple instanceof Array   // false
```

三、使用 Object.prototype.toString.call()判断                        
   call()方法可以改变this的指向，那么把Object.prototype.toString()方法指向不同的数据类型上面，返回不同的结果

### javascript --- for of和for in的区别？

结论：
  1. 推荐在循环对象属性的时候，使用for...in,在遍历数组的时候的时候使用for...of。
  2. for...in循环出的是key，for...of循环出的是value
  3. 注意，for...of是ES6新引入的特性。修复了ES5引入的for...in的不足
  4. for...of不能循环普通的对象，需要通过和Object.keys()搭配使用
使用for...in循环：
```
  for(let index in aArray){
    console.log(`${aArray[index]}`);
  }
```
使用for...of循环：
```
  for(var value of aArray){
      console.log(value);
  }
```

### let var const 区别
  1. let不允许在相同作用域内重复声明（报错同时使用var和let，两个let）
  2. var定义的变量，作用域是整个封闭函数，是全域的；let定义的变量，作用域是在块级或者字块中；
  3. 只要块级作用域内存在let，它所声明的变量就会绑定在这个区域；
  4. 变量提升：不论通过var声明的变量处于当前作用于的第几行，都会提升到作用域的最顶部。而let声明的变量不会在顶部初始化，凡是在let声明之前使用该变量都会报错（引用错误ReferenceError）；

  const用来专门声明一个常量，它跟let一样作用于块级作用域，没有变量提升，重复声明会报错，不同的是const声明的常量不可改变，声明时必须初始化（赋值）


### Set 实现并集、交集和差集。
```
  let a = new Set([1, 2, 3]);
  let b = new Set([4, 3, 2]);

  // 并集
  let union = new Set([...a, ...b]);
  // Set {1, 2, 3, 4}

  // 交集
  let intersect = new Set([...a].filter(x => b.has(x)));
  // set {2, 3}

  // （a 相对于 b 的）差集
  let difference = new Set([...a].filter(x => !b.has(x)));
  // Set {1}
```