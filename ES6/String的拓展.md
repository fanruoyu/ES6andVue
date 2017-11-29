# 字符串的拓展

## 1.Number.isFinite(), Number.isNaN()

ES6在Number对象上，新提供了两个方法。其中Number.isFinite()用来检测数值是否是一个有限的，对于一个非数值一律返回false他不会转换
    Number.isFinite(15); // true
    Number.isFinite(0.8); // true
    Number.isFinite(NaN); // false
    Number.isFinite(Infinity); // false
    Number.isFinite(-Infinity); // false
    Number.isFinite('foo'); // false
    Number.isFinite('15'); // false
    Number.isFinite(true); // false

Number.isNaN()只有对于NaN才返回true，非NaN一律返回false。
    Number.isNaN(NaN) // true
    Number.isNaN("NaN") // false
    Number.isNaN(1) // false

## 2.Number.parseInt(),Number.parseFloat()获取整数和浮点数

## 3.Number.isInteger(), 判断是否为一个整数，需要注意在JavaScript中整数和浮点数是一样的，如3，和3.0

## 4.Math对象的额拓展（常用的）

### Math.trunc()

用于去除一个数的小数部分，返回的是整数部分的值，
    Math.trunc(4.1) // 4
    Math.trunc(4.9) // 4
    Math.trunc(-4.1) // -4
    Math.trunc(-4.9) // -4
    Math.trunc(-0.1234) // -0

对于非数值，Math.trunc内部用Number方法将其转成了number形式的
    Math.trunc('123.456') // 123
    Math.trunc(true) //1
    Math.trunc(false) // 0
    Math.trunc(null) // 0

对于空值和无法截取的整数值返回的是NaN
    Math.trunc(NaN);      // NaN
    Math.trunc('foo');    // NaN
    Math.trunc();         // NaN
    Math.trunc(undefined) // NaN

### Math.sign()
用来判断一个数到底是不是正数，负数还有0.对于非数值，先转成数值。
他的返回值有五种值

参数为正数，返回+1；
参数为负数，返回-1；
参数为 0，返回0；
参数为-0，返回-0;
其他值，返回NaN。

    Math.sign(-5) // -1
    Math.sign(5) // +1
    Math.sign(0) // +0
    Math.sign(-0) // -0
    Math.sign(NaN) // NaN

对于那些取法转成数值的返回NaN
    Math.sign('')  // 0
    Math.sign(true)  // +1
    Math.sign(false)  // 0
    Math.sign(null)  // 0
    Math.sign('9')  // +1
    Math.sign('foo')  // NaN
    Math.sign()  // NaN
    Math.sign(undefined)  // NaN

### Math.cbrt()
用于计算一个数的立方根
    Math.cbrt(-1) // -1
    Math.cbrt(0)  // 0
    Math.cbrt(1)  // 1
    Math.cbrt(2)  // 1.2599210498948734

对于非数值，先使用Number的方法转成是指，然后再计算,不能转为数值的，返回的NaN
    Math.cbrt('8) // 2
    Math.cbrt('hello) // NaN


