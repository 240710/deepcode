# js学习

1. JavaScript是一种运行在客户端的脚本语言。

2. 由浏览器解释执行基于对象的脚本语言。弱类型语言：可以不声明直接使用

3. alert（“内容”）能控制浏览器弹出一个警告框

4. document.write("内容")向~<body>~中写入内容

5. console.log("内容")向控制台输出一个内容

6. 我们可以将js代码写在标签的onclick属性中，当我们点击按钮时js代码才会执行。

   ~~~javascript
   <button onclick="alert('hello')；">点我</button>
   ~~~

   也可以将js代码写在超链接的href属性里，当点击超链接时会执行js代码

   ~~~JavaScript
   <a href="javascript:alert('hello');">点我</a>
   ~~~

7. 和css一样我们可以将js代码编写到外部js文件中，然后通过script标签引入。

   ~~~JavaScript
   <script type="text/javascript" src="js/script.js"></script>
   ~~~

   **script标签一旦用于引入外部文件，就不能编写代码了。如果需要可以再添加一个script标签**

   ---

   

## 基本语法

+ 标识符

  就是给变量，函数，属性或函数的参数起名字，但是标识符第一个字母必须是一个字母，一个下划线，或$，其他字母除了上述几个外还有数字都是允许的

  **标识符不能是关键字和保留字符**

+ 字面量

  字面量实际上就是一些固定的值，比如：1、2 、3、true、false、null、NaN、“hello”，字面量都是不可以改变的，由于字面量不是很方便使用，所以在JavaScript中很少直接使用字面量，使用的而是变量。

+ 变量

  声明：使用var关键字声明变量

  ~~~javascript
  var a=123；
  ~~~

---

## 数据类型

JavaScript有5种基本数据类型

####字符串型（String）

####数值型（Number）

+ Number类型用来表示整数和浮点数（带有小数点的数）

+ **特殊的数字：**

  infinity：正无穷

  -infinity：负无穷

  NaN：非法数字

+ 使用typeof检查一个Number类型的数据时，会返回“number”

####布尔型（Boolean）

+ 只有**true和false**两种数值

####undefined型（Undefined）

+ 只有一个值，**undefined，在使用var声明变量但为对其赋值时变量值就是undefined**

####null型（Null）

+ Null类型也是只有一个值**null**（意义为空）

除此之外的类型都为Object类型

---

### 强制类型转换

#### 转换成String类型

+ 方式一：调用toString（）方法，**（null和undefined类型没有toString（）方法）**

  ~~~JavaScript
  var a = 123;
  a = a.toString();
  ~~~

+ 方式二：调用String函数，对于Number和Boolean类型其实就是调用了一次toString（）方法，而对于null和undefined就是将他们转换成了“null”和“undefined”

  ~~~JavaScript
  var a = 123;
  a = String(a);
  
  var b = undefined;
  b = String(b);
  
  var c = null;
  c = String(c);
  
  ~~~

+ 方式三：让这些数据类型的数加上一个**“ ”**（任何数据类型和String类型相加结果都是String类型）

  ~~~JavaScript
  var a = 123;
  a = a + "";
  ~~~

#### 转换成Number类型

+ 方式一：使用Number（）函数

  **1.字符串转换成数字**
  如果是纯数字的字符串，则直接将其转换为数字
  如果字符串中有非数字的内容，则转换为NaN
  如果字符串是一个空串或者是一个全是空格的字符串，则转换为0

  **2.布尔转换成数字**
  true 转成 1
  false 转成 0

  **3.null转换成数字**
  null 转成 0

  **4.undefined转换成数字**
  undefined 转成 NaN

  ~~~JavaScript
  var a=“123”;
  a = Number(a);
  ~~~

+ 方式二：利用parseInt() 把一个字符串转换为一个整数

  ~~~JavaScript
  var a = "123";
  a = parseInt(a);
  ~~~

+ 方式三：利用parseFloat() 把一个字符串转换为一个浮点数

  ~~~javascript
  var a = "123.456";
  a = parseFloat(a);
  ~~~

#### 转换成Boolean类型

想要将其它的数据类型转换为Boolean，只能使用Boolean()函数。

+ 数字转换成Boolean型

  除了0和NaN，其他都是true

+ String转换成Boolean型

  除了空串，其余的都是true

+ null和undefined都会转换成false

---

### 代码块

代码块是在大括号 {} 中所写的语句，以此将多条语句的集合视为一条语句来使用。

~~~javascript
{
    var a = 123;
    a++;
    alert(a);
}
~~~

---

### 对象

基本数据类型都是的单一的值，值与值间没有任何的联系，而对象是一种复合的数据类型在对象中可以保存多个数据类型的属性。

#### 对象的分类

+ 内建对象

  由ES标准定义的对象，如Math，Number，Boolean，Object……

+ 宿主对象

  由JS的运行环境提供的对象，目前来讲主要指浏览器提供的对象，如DOM，BOM

+ 自定义对象

  由开发人员自己创建的对象

#### 对象的创建

+ 第一种方式

  使用new关键字调用函数（构造函数）

  是专门用来创建对象的函数

  ~~~JavaScript
  var person = new Object();
  person.name = "孙悟空";
  person.age = 18;
  console.log(person);
  ~~~

  

+ 第二种方式

  使用对象字面量来创建对象

  **var 变量名={}；**

  ~~~JavaScript
  var person = {
      name: "孙悟空",
      age: 18
  };
  console.log(person);
  ~~~

  **注意：在第二种方式中，变量赋值不是用的=而是用的：**

#### 读取属性

+ 使用**对象.属性名**来访问

+ 使用**对象[’属性名‘]**来访问

  **如果读取对象中没有的属性，不会报错而是会返回undefined**

#### 删除属性

使用**delete**关键字

格式为：**delete 对象.属性名**

#### 对象与栈和堆的联系

在js运行时数据是保存到栈和堆的内存中的，简单来说栈内存用来保存变量和基本类型，堆内存是用来保存对象。

我们在声明一个变量时，实际上就是在栈内存中创建了一个空间用来保存变量。但是由于对象是一个引用数据，其真正的数据是保存在堆里面的。栈中的变量有一个地址值去对应堆中关于这个变量的数据。

因此当我们将一个对象赋给另一个对象时，其实是将栈中的地址值赋给了这个对象，两个对象都对应着同一个堆里的同一个数据。

---

### 函数

函数也是一个对象

函数可以封装一些功能（代码），在需要时可以调用执行这些功能

####创建函数

+ 使用函数对象来创建一个函数（很少用）

  ~~~JavaScript
  var 函数名 = new Function("执行语句");
  ~~~

  

+ 使用函数声明来创建一个函数（较常用）、

  ~~~JavaScript
  function 函数名([形参1,形参2,...,形参N]) {
      语句...
  }
  ~~~

  

+ 使用函数表达式来创建一个函数（较常用）

~~~JavaScript
var 函数名  = function([形参1,形参2,...,形参N]) {
    语句....
}
~~~

#### 函数的调用

+ 对于无参数的函数的调用

**函数名（）；**

+ 有参函数的调用

**函数名（实参值1，实参值2，……）**

####函数的返回值

我们可以使用return来设置函数的返回值，return后的值将会作为函数的执行结果返回。

**注意**：函数中在return后面的语句都不会执行，如果return后面不跟任何值就相当于返回了一个undefined，不写return也会返回undefined

~~~JavaScript
function sum(num1, num2) {
    return num1 + num2;
}

var result = sum(10, 20);
console.log(result);
~~~

#### 嵌套函数

在函数中声明的函数就是嵌套函数，嵌套函数只能在当前函数中可以访问，在当前函数外无法访问。

~~~JavaScript
function fu() {
    function zi() {
        console.log("我是子")
    }

    zi();
}

fu();
~~~

#### 匿名函数

没有名字的函数就是匿名函数，它可以让一个变量来接收

~~~JavaScript
function(a,b){
    console.info( a+b );
}
~~~



#### 立即执行函数

函数定义完，立即被调用，这种函数叫做立即执行函数，立即执行函数往往只会执行一次。

~~~JavaScript
(function () {
    alert("我是一个匿名函数");
})();
~~~

#### 对象中的函数

对象的属性值可以是任何的数据类型，也可以是函数

如果一个函数作为一个对象的属性保存，那么我们称这个函数是这个对象的方法，调用这个函数就说调用对象的方法（method）。

**注意：方法和函数只是叫法不同**

~~~JavaScript
var person = {
    name: "zhangsan",
    age: 18,
    sayHello: function () {
        console.log(name + " hello")
    }
}

person.sayHello();
~~~

---

### 作用域

作用域指一个变量的作用的范围

~~~JavaScript
function outFun2() {
    var inVariable = "内层变量2";
}
outFun2();
console.log(inVariable); // Uncaught ReferenceError: //inVariable is not defined
~~~

**变量inVariable在全局作用域没有声明，所以在全局作用域下取值会报错，这个变量变量只在函数范围内有效**

在JS中一共有两种作用域：

- **全局作用域**

  -直接编写在script标签中的js代码，都在全局作用域

  -全局作用域在页面打开时创建，在页面关闭时销毁

  -在全局作用域中有一个全局对象window

  ​     它代表的是一个浏览器的窗口，由浏览器创建，可以直接使用。

  -在全局作用域中：

  ​	创建的变量都会作为window对象的属性保存

  ​	创建的函数都会作为window对象的方法保存

  ​	全局作用域中的变量都是全局变量，在页面的任意的部分都可以调用

  ~~~JavaScript
  <script>
      var a=10;
      var b=20;
       
      console.log(window.a+window.b);
  
  	function fun (){
          console.log("我是fun函数");
      }
  
  	window.fun();
   </script>
  ~~~

  

- **函数作用域**

  -调用函数时创建函数作用域，函数执行完毕以后，函数作用域销毁

  -每调用一次函数就会创建一个新的函数作用域，它们之间是互相独立的

  -在函数作用域中可以访问到全局作用域的变量，在全局作用域中无法访问到函数作用域的变量

  -在函数中要访问全局变量可以使用window对象

  ~~~JavaScript
  <script>
        function fn(){
           var innerVar = "inner";
        }
        fn();
        console.log(innerVar);// ReferenceError: innerVar is not defined
  </script>
  ~~~

  **需要注意的是，函数内部声明变量的时候，一定要使用var命令。如果不用的话，实际上就是声明了一个全局变量！**

  #### 作用域链

  **作用域链是由多个具有上下级关系的作用域形成的链**，如函数作用域和全局作用域就是上下级关系，函数为下，全局为上。

  当需要查找变量时就要沿着作用域链来查找。

  在查找是按照如下的规则：

  1. 在当前作用域下的执行上下文中查找对应的属性，如果有直接返回，否则进入2

  2. 在上一级作用域的执行上下文中查找对应的属性，如果有直接返回，否则进入3

  3. 再次执行2的相同操作，直到全局作用域，如果还找不到就抛出找不到的ReferenceError异常

     

  