# 数组的拓展

## 1.拓展运算符

### 含义 

拓展运算符spread是三个点（....）它毫不rest参数的逆运算，僵硬额数组转为用多好分割的参数序列。

```js
    console.log(...[1, 2, 3])
    // 1 2 3

    console.log(1, ...[2, 3, 4], 5)
    // 1 2 3 4 5

    [...document.querySelectorAll('div')]
    // [<div>, <div>, <div>]
```
如果拓展符后面是一个空数组，则不产生任何结果
[...[], 1] // [1]

## 2.替换数组的apply方法

有雨拓展符可以展开数组，所以不再需要apply方法，将数组转为函数的参数了。

## 3.拓展符号应用

### 1.赋值数组

```js
    const a1 = [1, 2];
    const a2 = a1;
    a2[0] = 2;
    a1 // [2, 2]
```
上面代码说明了a2并不是a1的克隆，二十指向同一个数据的指针，修改a2，a1也会被修改
拓展福提供了复制数组的简便方法

```js
    const a1 = [1, 2];
    // 方法一
    const a2 = [...a1];
    // 方法二
    const [...a2] = a1
```

### 2.合并数组

拓展运算提供了数组合并的新写法

```js
    //ES5
    [1, 2].concat(moew)
    // ES6
    [1, 2, ...more]
```
### 3. 与结构赋值结合
```js
    const [first, ...rest] = [1, 2, 3, 4, 5];
    first // 1
    rest  // [2, 3, 4, 5]

    const [first, ...rest] = [];
    first // undefined
    rest  // []

    const [first, ...rest] = ["foo"];
    first  // "foo"
    rest   // []
```
拓展符只能放在参数最后，否则报错
```js
    const [...butLast, last] = [1, 2, 3, 4, 5];
    // 报错

    const [first, ...middle, last] = [1, 2, 3, 4, 5];
    // 报错
```
### 4.字符串
```js
    [...'hello']
    // [ "h", "e", "l", "l", "o" ]
```

## 4.Array.from()

用于将两类对象转为真正的数组:类似于数组的对象和可遍历的对象
```js
    let arrayLike = {
        '0': 'a',
        '1': 'b',
        '2': 'c',
        length: 3
    };

    // ES5的写法
    var arr1 = [].slice.call(arrayLike); // ['a', 'b', 'c']

    // ES6的写法
    let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
```

实际应用中，常见的类似于数字的对象是DOM操作返回的NodeList集合，以及函数内部的argument对象。A仍然有.from()都可以将他们转为真正的数组。
```js

    // NodeList对象
    let ps = document.querySelectorAll('p');
    Array.from(ps).forEach(function (p) {
    console.log(p);
    });

    // arguments对象
    function foo() {
    var args = Array.from(arguments);
    // ...
}
```
以上代码中，querySelectoeAll方法返回的是一个类似于数组的对象，可以将这个对象转为真正的数组，在使用forEach方法。

## Array.of()将一组值，转为数组。
```js

    Array.of(3, 11, 8) // [3,11,8]
    Array.of(3) // [3]
    Array.of(3).length // 1 
```
该方法的目的是，弥补数组构造函数Array的不足，因为参数个数的不同，会导致Array()的行为有差异。

```js

    Array() // []
    Array(3) // [, , ,]
    Array(3, 11, 8) // [3, 11, 8]
```

Array.of基本上可以用来替代Array()或new Array()，并且不存在由于参数不同而导致的重载。它的行为非常统一。

```js
    Array.of() // []
    Array.of(undefined) // [undefined]
    Array.of(1) // [1]
    Array.of(1, 2) // [1, 2]
```

