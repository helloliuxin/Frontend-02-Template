## 学习笔记

### 一、语言按语法分类
-  非形式语言
   - 中文、英文

- 形式语言（乔姆斯基谱系）
  - 0型 无限制文法
  - 1型 上下文相关文法
  - 2型 上下文无关文法
  - 3型 正则文法

> 在乔姆斯基谱系中0、1、2、3这四型文法是上下包含关系

### 二、产生式（BNF）
- 用尖括号括起来的名称来表示语法结构名
- 语法结构分成基础结构和需要用其他语法结构定义的复合结构 
  - 基础结构称为终结符
  - 复合结构称非终结符
- 引号和中间的字符表示终结符
- 可以有括号
- *表示重复多次
- |表示或
- +表示至少一次

**BNF中常用的元字符及其表示的意义如下：**
1. 在双引号中的字 "word" 代表着这些字符本身。而double_quote用来代表双引号；
2. 在双引号外的字（有可能有下划线）代表着语法部分；
3. 尖括号 < > 内包含的为必选项；
4. 方括号 [ ] 内包含的为可选项；
5. 大括号 { } 内包含的为可重复0至无数次的项；
6. 圆括号 ( ) 内包含的所有项为一组，用来控制表达式的优先级；
7. 竖线 | 表示在其左右两边任选一项，相当于"OR"的意思；
8. ::= 是“被定义为”的意思；
9. ...  表示术语符号；
10. 斜体字: 参数，在其它地方有解释；

`参考文章：` 
1. [语法格式描述规范BNF和ABNF](https://www.jianshu.com/p/15efcb0c06c8)
2. [巴科斯-诺尔（BNF范式）范式](https://www.geek-share.com/detail/2501404822.html)

### 三、通过产生式理解乔姆斯基谱系
  - 0型 无限制文法
    - ?::=?
  - 1型 上下文相关文法
    - ?<`A`>?::=?<`B`>?
  - 2型 上下文无关文法
    - <`A`>::=?
  - 3型 正则文法
    - <`A`>::=<`A`>?

JS总体来说属于上下文无关文法，除了个别例外


### 四、语言的分类
**1. 形式语言按`用途`来分可以分为以下两种**
- 数据描述语言
  ```
  JSON, HTML, XAML, SQL, CSS
  ```
- 编程语言
  ```
  C, C++, Java, C#, Python, Ruby, Perl, Lisp, T-SQL, Clojure, Haskell, JavaScript
  ```

**2. 形式语言按`表达方式`来分可以分为以下两种**
- 声明式语言
  ```
  JSON, HTML, XAML, SQL, CSS, Lisp, Clojure, Haskell
  ```
- 命令式语言
  ```
  C, C++, Java, C#, Python, Ruby, Perl, JavaScript
  ```

### 五、编程语言的性质
- 图灵完备性
  
  在可计算性理论里，如果一系列操作数据的规则（如指令集、编程语言、细胞自动机）按照一定的顺序可以计算出结果，被称为图灵完备（turing complete）。

  `参考文章：` [图灵完备到底是个什么鬼?](https://www.jianshu.com/p/a04b16c5bbda)

- 动态和静态

  **动态：** 
   - 在用户的设备/在线服务器上
   - 产品实际运行时
   - Runtime

  **静态**
   - 在程序员的设备上
   - 产品开发时
   - Compiletime


- 类型系统
  - 动态类型系统与静态类型系统
  - 强类型与弱类型
  - 复合类型
    - 结构体
    - 函数签名
  - 子类型
  - 泛型
    - 逆变/协变

## JS的其中类型

### Null
- 只有一个值 null
- null是JS里的保留关键字，不能做变量名 例如：let null = 0; // 报错

### Undefined
- 未定义 只有一个值 undefined
- 不是关键字，只是一个变量;
- 全局变量 可作变量名 let undefined = 0; // 不报错
- 避免无意中被篡改，建议使用void 0来获取undefined的值

### Number
- IEEE 754 Double Float (双精度浮点类型)
  - Sign(1) —— 符号位， 0代表正数 1代表复数
  - Exponent(11) —— 指数， 决定浮点数的范围
  - Fraction(52) —— 有效位数， 决定浮点数的精度
- 表示方法
  - 二进制
  - 八进制
  - 十进制
  - 十六进制
- NaN Infinity -Infinity
- 根据浮点数的定义，非整数的Number类型无法用==(===也不行)来比较

```js
console.log(0.1 + 0.2 == 0.3); //这里输出的结果是false，说明两边不相等的，这是浮点运算的特点，浮点数运算的精度问题导致等式左右的结果并不是严格相等，而是相差了个微小的值。

console.log(Math.abs(0.1 + 0.2 - 0.3) <= Number.EPSILON); //正确的比较方法是使用 JavaScript 提供的最小精度值：
```

`参考资料：` 
1. [深入理解IEEE754的64位双精度](https://www.boatsky.com/blog/26)
2. [IEEE754标准 单精度(32位)/双精度(64位)浮点数解码](https://blog.csdn.net/abcdu1/article/details/75095781)


### String
- 基础
  - Chartacter —— 字符
  - Code Point —— 码点
  - Encoding —— 编码方式
- 常见的编码
  - ASCII
  - Unicode
  - UCS
  - GB
  - ISO-8859
  - BIG5
- String有最大长度是2^53-1
- UTF
- ''  ""
- `${a}a`

`参考资料：`
1. [字符编码笔记：ASCII，Unicode 和 UTF-8](http://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html)
2. [通过javascript进行UTF-8编码](https://www.cnblogs.com/doublenet/p/5616451.html)


### Boolean
- true
- false

### Object
- 案例
  - 三只一模一样的鱼，其实是三个对象。
  - 其中一只鱼发生状态改变（失去了尾巴），其他两只鱼不受影响。
  - 因此，当我们在计算机中描述这三只鱼时，必须把相同的数据存三份。


- 总结
  - 任何一个对象都是唯一的，这与它本身的状态无关
  - 所以即使状态完全一样的两个对象，也并不相等
  - 我们用状态描述对象
  - 我们状态的改变即是对象
  - `我们不应该受到语言描述的干扰。在设计对象的状态和行为时，我们总是遵循 “行为改变状态”的原则。`


- class
  - 类是一种常见的描述对象 的方式。
  - ”归类”和”分类”则 是两个主要的流派。
  - 对于”归类”方法而言， 多继承是非常自然的事情。 如C++
  - 而采用分类思想的计算机 语言，则是单继承结构。 并且会有一个基类Object。

- Prototype
  - 原型是一种更接近人类原始认知的描述对象的方法；
  - 我们并不试图做严谨的分类，而是采用“相似”这样的方式去描述对象；
  - 任务对象仅仅需要描述他自己与原型的区别即可。

- Object in JavaScript
  - 基础概念
    - 在 JavaScript 运行时，原生对象的描述方式非常简单，只需要关系原型和属性两个部分；
    - 属性可以用来描述状态和行为（其函数可以放进属性里）；
    - 用内存地址的唯一性来表示对象的唯一性；
    - 原型机制：当去找一个对象的属性的时候，如果它自身不包含该属性就会去原型上找，如果原型的原型不为空的话，会继续往原型的原型上找，所有就形成了原型链这样一个行为（沿着原型的指向一直往上找，直到原型为 null）。

  - 属性
    - JavaStript 用属性来统一抽象对象的状态和行为；
    - 一般来说，数据属性用于描述状态，访问器属性用于描述行为；
    - 数据属性中如果存储函数，也可以用于描述行为； *原型机制
    - 当我们访问属性时，如果当前对象没有，则会沿着原型找原型对象是否有此名称的属性，而原型对象还可能有原型，因此会有原型链这一说法；
    - 这一算法保证了，每个对象只需要描述自己和原型的区别即可；

  - API
    - {}. [] Object.defineProperty
    - Object.create / Object.setPrototypeOf / Object.getPrototypeOf
    - new / class / extends
    - new / function prototype

  - Function Object
    - 前面讲述了 JavaScript 中的一般对象，但 JavaScript 中还有一些特殊的对象，比如函数对象；
    - 除了一般对象的属性和行为，函数对象还有一个行为[call]；
    - 我们用 JavaScript 中的 function 关键字、箭头运算符或者 function 构造器创建对象，会有[call]这个行为；
    - 我们用了些 f()这样的语法把对象当着函数调用时，会访问到[[call]]这个行为，如果对应的对象没有[[call]]行为，则会报错；

- 总结
  - JavaScript 中的几个基本类型，都在对象类型中有一个“亲戚”。它们是：
    - Number
    - String
    - Boolean
    - Symbol
  - 所以，我们必须认识到 3 与 new Number(3) 是完全不同的值，它们一个是 Number 类型，一个是对象类型。
  - Symbol 函数比较特殊，直接用 new 调用它会抛出错误，但它仍然是 Symbol 对象的构造器。
  - 我们在原型上添加方法，都可以应用于基本类型，比如以下代码，在 Symbol 原型上添加了 hello 方法，在任何 Symbol 类型变量都可以调用。
  
  ```js
  Symbol.prototype.hello = () => console.log("hello");
  var a = Symbol("a");
  console.log(typeof a); //symbol，a并非对象
  a.hello(); //hello，有效
  ```
  - `.` 运算符提供了装箱操作，它会根据基础类型构造一个临时对象，使得我们能在基础类型上调用对应对象的方法。


### Symbol
- 它是一切非字符串的对象key的集合，在ES6规范中，整个对象系统被用Symbol重塑

### **类型转换**
*JS 是弱类型语言，所以类型转换发生非常频繁，大部分运算都会先进行类型转换。大部分类型转换符合人类的直觉，但是如果不去理解类型转换的严格定义，很容易造成一些代码中的判断失误。*

- StringToNumber
  - 字符串到数字的类型转换，存在一个语法结构，类型转换支持十进制、二进制、八进制和十六进制，比如：30；0b111；0o13；0xFF。
  - 此外，JavaScript 支持的字符串语法还包括正负号科学计数法，可以使用大写或者小写的 e 来表示：1e3；-1e-2。需要注意的是，parseInt 和 parseFloat 并不使用这个转换，所以支持的语法跟这里不尽相同。
  - 在不传入第二个参数的情况下，parseInt 只支持 16 进制前缀“0x”，而且会忽略非数字字符，也不支持科学计数法。
  - 在一些古老的浏览器环境中，parseInt 还支持 0 开头的数字作为 8 进制前缀，这是很多错误的来源。所以在任何环境下，都建议传入 parseInt 的第二个参数，而 parseFloat 则直接把原字符串作为十进制来解析，它不会引入任何的其他进制。
  - 多数情况下，Number 是比 parseInt 和 parseFloat 更好的选择。

- NumberToString
  
  在较小的范围内，数字到字符串的转换是完全符合你直觉的十进制表示。当 Number 绝对值较大或者较小时，字符串表示则是使用科学计数法表示的。这个算法细节繁多，我们从感性的角度认识，它其实就是保证了产生的字符串不会过长。

- 装箱转换
  - 每一种基本类型 Number、String、Boolean、Symbol 在对象中都有对应的类，`所谓装箱转换，正是把基本类型转换为对应的对象，它是类型转换中一种相当重要的种类`。
  - 全局的 `Symbol 函数无法使用 new 来调用`，但我们仍可以利用装箱机制来得到一个 Symbol 对象，我们可以利用一个函数的 call 方法来强迫产生装箱。

  ```js
  var symbolObject = function() {
    return this;
  }.call(Symbol("a"));
  console.log(typeof symbolObject); //object
  console.log(symbolObject instanceof Symbol); //true
  console.log(symbolObject.constructor == Symbol); //true
  ```

  - 装箱机制会频繁产生临时对象，在一些对性能要求较高的场景下，我们应该尽量避免对基本类型做装箱转换。使用内置的 Object 函数，我们可以在 JavaScript 代码中显式调用装箱能力。

  ```js
  var symbolObject = Object(Symbol("a"));
  console.log(typeof symbolObject); //object
  console.log(symbolObject instanceof Symbol); //true
  console.log(symbolObject.constructor == Symbol); //true
  ```

  - 每一类装箱对象皆有私有的 Class 属性，这些属性可以用 Object.prototype.toString 获取
  
  ```js
  var symbolObject = Object(Symbol("a"));
  console.log(Object.prototype.toString.call(symbolObject)); //[object Symbol]
  ```

  - 在 JavaScript 中，没有任何方法可以更改私有的 Class 属性，因此 Object.prototype.toString 是可以准确识别对象对应的基本类型的方法，它比 instanceof 更加准确。但需要注意的是，call 本身会产生装箱操作，所以需要配合 typeof 来区分基本类型还是对象类型。

- 拆箱装换
  - 在 JavaScript 标准中，规定了 ToPrimitive 函数，它是对象类型到基本类型的转换（即，拆箱转换）。
  - 对象到 String 和 Number 的转换都遵循“先拆箱再转换”的规则。通过拆箱转换，把对象变成基本类型，再从基本类型转换为对应的 String 或者 Number。
  - 拆箱转换会尝试调用 valueOf 和 toString 来获得拆箱后的基本类型。如果 valueOf 和 toString 都不存在，或者没有返回基本类型，则会产生类型错误 TypeError。

  ```js
  var o = {
    valueOf: () => {
      console.log("valueOf");
      return {};
    },
    toString: () => {
      console.log("toString");
      return {};
    },
  };
  o * 2;
  // valueOf
  // toString
  // TypeError
  ```
  - 到 String 的拆箱转换会优先调用 toString。我们把刚才的运算从 o*2 换成 String(o)，那么会看到调用顺序就变了。
  ```js
  var o = {
    valueOf: () => {
      console.log("valueOf");
      return {};
    },
    toString: () => {
      console.log("toString");
      return {};
    },
  };
  String(o);
  // toString
  // valueOf
  // TypeError
  ```


### 单词
1. atom n. 原子
2. expression n. 表达式
3. statement n. 语句，声明
4. structure 结构，构造
5. program 程序
6. grammar n. 语法；语法书
7. literal n. 字面；文字；常量
8. variable adj. 变量的；变量；变数
9. line terminator 行终结符
10. execution n. 执行；完成；实行
11. context n. 环境；语境；上下文
12. sign n. 符号
13. exponent n. 指数
14. fraction n. 分数；进度位