#javascript高级程序设计第三章(基本概念)
Boolean()转为布尔值
ifFinite()验证是不是在最大值跟最小值之间
isNaN()判断是否数字 true为不是一个number
转化为数字的方法
Number()  字符窜返回NAN
parseInt(str,进制数) 	第一个是数字后面是字符窜返回前面数字
parseFloat()第一个小数点会转化为  只返回十进制
.length可以访问长度
toString() String()转为字符窜
对象的每个实例都有下列属性和方法
construtor
hasOwnProperty检测是否有这个实例
isPrototypeOf()用于检查是否传入对象的原型
propertyIsEnumerable()能否被枚举
toString valueOf toLocaleString返回字符窜
function()可以传任意参数  arguments[0]表示第一个参数


小结
  ECMAScript 中的基本数据类型包括 Undefined 、 Null 、 Boolean 、 Number 和 String 。
  与其他语言不同，ECMScript 没有为整数和浮点数值分别定义不同的数据类型， Number 类型可
用于表示所有数值。
  ECMAScript 中也有一种复杂的数据类型，即 Object 类型，该类型是这门语言中所有对象的基
础类型。
  严格模式为这门语言中容易出错的地方施加了限制。
  ECMAScript 提供了很多与 C 及其他类 C 语言中相同的基本操作符，包括算术操作符、布尔操作
符、关系操作符、相等操作符及赋值操作符等。
  ECMAScript 从其他语言中借鉴了很多流控制语句，例如 if 语句、 for 语句和 switch 语句等。
ECMAScript 中的函数与其他语言中的函数有诸多不同之处。
  无须指定函数的返回值，因为任何 ECMAScript 函数都可以在任何时候返回任何值。
  实际上，未指定返回值的函数返回的是一个特殊的 undefined 值。
  ECMAScript 中也没有函数签名的概念，因为其函数参数是以一个包含零或多个值的数组的形式
传递的。
  可以向 ECMAScript 函数传递任意数量的参数，并且可以通过 arguments 对象来访问这些参数。
  由于不存在函数签名的特性，ECMAScript 函数不能重载
