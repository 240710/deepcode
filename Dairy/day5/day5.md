# day5

## vue2

### vue.js的模板语句

Vue.js 的核心是一个允许你采用简洁的模板语法来声明式的将数据渲染进 DOM 的系统。

结合响应系统，在应用状态改变时， Vue 能够智能地计算出重新渲染组件的最小代价并应用到 DOM 操作上。

**在vue中不需要去关心怎么更改Dom元素，而是将重点放在如何更改数据**

~~~html
<div id="app">
    <div >{{message}}</div>
</div>
    
<script>
new Vue({
  el: '#app',
  data: {
    message: 'hello,vue'
  }
})
</script>
~~~

上述的代码中利用**{{  }}**里面的文本来插值，就像代码里的message会由于script标签里面的message信息的改变而改变。

代码中的el表示**挂载点**，后面的#app是id选择器（也可以是其他选择器），表明Vue对象中的变化是针对选择器选中的元素的，**及其内部的后代元素。**

data表示**数据对象**，后面的代码块就是div中被选来插值的文本的信息的赋值。

---



  ### 用vue开发网页效果

#### vue指令

**v-text**：设置标签的文本值

~~~html
<div id="app">
    <h1 v-text="message"></h1>
</div>
<script>
var app=newVue({
    el:"#app",
    data:{
        message:"hello,vue"
    }    
})
</script>    
~~~

上述代码的效果和用{{message}}是差不多的，**但是一旦用了v-text其所在的标签的全部内容就会全部被替换成data中的内容**，v-text="message"中也可以通过+来进行连接，如v-text="message+‘！’"

---



**v-html**：设置标签的innerHTML

~~~html
<div id="app">
    <h1 v-html="message"></h1>
</div>
<script>
var app=newVue({
    el:"#app",
    data:{
        message:"<a href='javascript'>hello,vue!</a>"
    }    
})
</script>    
~~~

于v-text不同的是，**使用v-html可以为选中的元素设置一个html结构。**

---



**v-on**：为元素绑定事件

~~~html
<div id="app">
   <input type="button" value="v-on指令" v-on:click="doIt">
</div>
<script>
var app=newVue({
    el:"#app",
    method：{
    doIt:function（）{
        alert("hello vue!")；
    } 
    }
})
</script>    
~~~

其中，**代码里的v-on:click="doIt"的格式其实是v-on:事件名="方法名"**，而且v-on其实可以写成@，**@:click="doIt"**，**方法放在method属性中**

补充：

**v-on还可以用来传递自定义参数，事件修饰符**

~~~html
<div id="app">
   <input type="button" value="v-on指令" v-on:click="doIt（参数）">
   <input type="button" value="v-on指令" v-on:keyup.enter="doIt（参数）">
	//v-on:keyup.enter中的。enter就是事件修饰符表示点击enter键后就会触发事件
</div>
<script>
var app=newVue({
    el:"#app",
    method：{
    doIt:function（p1）{//定义了一个形参p1
        alert("hello vue!")；
		 alert(p1)；//参数
    } 
    }
})
</script> 
~~~



---



**v-show**：根据表达值的真假，切换元素的显示和隐藏。true是显示，false是隐藏

~~~html
<div id="app">
    <h1 v-show="isshow"></h1>
</div>
<script>
var app=newVue({
    el:"#app",
    data:{
        isshow:true;
    }    
})
</script>    
~~~

原理是修改元素的display状态。

---



**v-if**：根据表达式的真假，切换元素的显示和隐藏（操纵Dom元素）

~~~html
<div id="app">
    <h1 v-if="isshow"></h1>
</div>
<script>
var app=newVue({
    el:"#app",
    data:{
        isshow:true;
    }    
})
</script>    
~~~

v-if和v-show效果是类似的，但是v-if是操纵的dom元素，当表达式为true时元素存在于dom树中，为fales时，从dom树中清除。**性能消耗会大一些**

---



**v-bind:**设置元素的属性

~~~html
<div id="app">
    <img v-bind：src="imgsrc"></img>
</div>
<script>
var app=newVue({
    el:"#app",
    data:{
        imgsrc:“JavaScript”
    }    
})
</script>    
~~~

**v-bind：src="imgsrc"**也可以简写成   **：src="imgsrc"**

---



**v-for**根据数据生成列表结构，数组经常和v-for结合使用

语法：**（item，index）in 数据**

其中item代表每一项，index代表索引，是可以更改的（只要符合命名要求）

数组长度的更新会同步到页面上，是响应式的

 ~~~html
 <div id="app">
     <ul>
         <li v-for=“itme in arr”>
             {{item}}
         </li>
     </ul>
 </div>
     
 <script>
 new Vue({
   el: '#app',
   data: {
    arr:[“北京”，“上海”，“广州”，“南京”]
   }
 })
 </script>
 ~~~

效果是

+ 北京

+ 上海

+ 广州

+ 南京

  ---

  

**v-model**获取和设置**表单元素**的值（**双向数据绑定**）

~~~html
<div id="app">
   <input type="text" v-model=“message” />
</div>
<script>
var app=newVue({
    el:"#app",
    data:{
      message:"hello vue"  
    }
})
</script>    
~~~

data里的数据和v-madel的message一方改变另一方也会随之改变（双向数据绑定）

---



##Es6

### let与const

与var不同，var声明的变量是全局变量，在全局范围内有效，而let 声明的变量只在 let 命令所在的代码块内有效，且let不能重复声明，只能声明一次。

~~~JavaScript
{
  let a = 0;
  a   // 0
}
a   // 报错 ReferenceError: a is not defined
~~~

let不存在变量提升，而var存在变量提升。

~~~html
console.log(a);  //ReferenceError: a is not defined
let a = "apple";
 
console.log(b);  //undefined
var b = "banana";
~~~

变量 b 用 var 声明存在变量提升，所以当脚本开始运行的时候，b 已经存在了，但是还没有赋值，所以会输出 undefined。

变量 a 用 let 声明不存在变量提升，在声明变量 a 之前，a 不存在，所以会报错

**变量提升即变量可以先使用再声明**

const 声明一个只读的常量，一旦声明，常量的值就不能改变。**这意味着，一旦声明必须初始化，否则会报错。**

~~~JavaScript
const PI = "3.1415926";
PI  // 3.1415926

const MY_AGE;  // SyntaxError: Missing initializer in const declaration    
~~~

**暂时性死区:**

~~~JavaScript
var PI = "a";
if(true){
  console.log(PI);  // ReferenceError: PI is not defined
  const PI = "3.1415926";
}
~~~

**再ES6 中明有确的规定，代码块内如果存在 let 或者 const，代码块会对这些命令声明的变量从块的开始就形成一个封闭作用域。这就意味着代码中的变量PI无法在if语句的代码块中调用，需要再进行定义，否则会报错。**

---



###解构赋值

解构赋值是对赋值运算符的扩展。**（就是对 = 这个赋值运算符扩展更多的用法，以此来应变实际需求）**

他是一种针对数组或者对象进行模式匹配，然后对其中的变量进行赋值。

**数组模型的解构**

基本形式

~~~JavaScript
let [a, b, c] = [1, 2, 3];
// a = 1
// b = 2
// c = 3
~~~

嵌套形式

~~~javas
let [a, [[b], c]] = [1, [[2], 3]];
// a = 1
// b = 2
// c = 3
~~~

可忽略形式

~~~JavaScript
let [a, , b] = [1, 2, 3];
// a = 1
// b = 3
~~~

**剩余运算符**

~~~JavaScript
let [a, ...b] = [1, 2, 3];
//a = 1
//b = [2, 3]
~~~

不完全解构

~~~JavaScript
let [a = 1, b] = []; // a = 1, b = undefined
~~~

**字符串形式等**

在数组的解构中，解构的目标若为可遍历对象，皆可进行解构赋值。可遍历对象即实现 Iterator 接口的数据。

~~~JavaScripts
let [a, b, c, d, e] = 'hello';
// a = 'h'
// b = 'e'
// c = 'l'
// d = 'l'
// e = 'o'
~~~

解构默认值

当解构模式有匹配结果，且匹配结果是 undefined 时，会触发默认值作为返回结果。

~~~JavaScript
let [a = 3, b = a] = [];     // a = 3, b = 3匹配结果为undefined
let [a = 3, b = a] = [1];// a = 1, b = 1a的匹配结果为1，b的匹配结果为undefined
let [a = 3, b = a] = [1, 2]; // a = 1, b = 2正常解构赋值
~~~

---



**对象模型的解构**

基本

~~~JavaScript‘
let { foo, bar } = { foo: 'aaa', bar: 'bbb' };
// foo = 'aaa'
// bar = 'bbb'
 
let { baz : foo } = { baz : 'ddd' };
// foo = 'ddd'
~~~

可嵌套可忽略

~~~JavaScript
let obj = {p: ['hello', {y: 'world'}] };
let {p: [x, { y }] } = obj;
// x = 'hello'
// y = 'world'
let obj = {p: ['hello', {y: 'world'}] };
let {p: [x, {  }] } = obj;
// x = 'hello'
~~~

不完全解构

~~~JavaScript
let obj = {p: [{y: 'world'}] };
let {p: [{ y }, x ] } = obj;
// x = undefined
// y = 'world'
~~~

**剩余运算符**

~~~JavaScript
let {a, b, ...rest} = {a: 10, b: 20, c: 30, d: 40};
// a = 10
// b = 20
// rest = {c: 30, d: 40}
~~~

解构默认值

~~~JavaScript
let {a = 10, b = 5} = {a: 3};
// a = 3; b = 5;
let {a: aa = 10, b: bb = 5} = {a: 3};
// aa = 3; bb = 5;
~~~

---

###Symbol

ES6 引入了一种新的原始数据类型 Symbol ，表示独一无二的值，最大的用法是用来定义对象的唯一属性名。

**基本用法**

Symbol 函数栈不能用 new 命令，因为 Symbol 是原始数据类型，不是对象。可以接受一个字符串作为参数，为新创建的 Symbol 提供描述，用来显示在控制台或者作为字符串的时候使用，便于区分。

~~~JavaScript
let sy = Symbol("KK");
console.log(sy);   // Symbol(KK)
typeof(sy);        // "symbol"
 
// 相同参数 Symbol() 返回的值不相等（因为任何一个Symbol都是独一无二的）
let sy1 = Symbol("kk"); 
sy === sy1;       // false
~~~

**作为属性名时**

由于每一个 Symbol 的值都是不相等的，所以 Symbol 作为对象的属性名，可以保证属性不重名。

~~~JavaScript
let sy = Symbol("key1");
 
// 写法1
let syObject = {};
syObject[sy] = "kk";
console.log(syObject);    // {Symbol(key1): "kk"}
 
// 写法2
let syObject = {
  [sy]: "kk"
};
console.log(syObject);    // {Symbol(key1): "kk"}
 
// 写法3
let syObject = {};
Object.defineProperty(syObject, sy, {value: "kk"});
console.log(syObject);   // {Symbol(key1): "kk"}
~~~

Symbol 作为对象属性名时不能用（ . ）运算符调用，要用方括号。因为（ . ）运算符后面是字符串，所以取到的是字符串 sy 属性，而不是 Symbol 值 sy 属性。

~~~javascript
let syObject = {};
syObject[sy] = "kk";
 
syObject[sy];  // "kk"
syObject.sy;   // undefined
~~~

**注意点**：

Symbol 值作为属性名时，该属性是公有属性不是私有属性，可以在类的外部访问。但是不会出现在 for...in 、 for...of 的循环中，也不会被 Object.keys() 、 Object.getOwnPropertyNames() 返回。如果要读取到一个对象的 Symbol 属性，可以通过 Object.getOwnPropertySymbols() 和 Reflect.ownKeys() 取到。

**用来定义常量时，因为Symbol的值时唯一的，所以不会出现相同的值的常量。**

**Symbol.for()**

Symbol.for() 首先会在全局搜索被登记的 Symbol 中是否有该字符串参数作为名称的 Symbol 值，如果有即返回该 Symbol 值，若没有则新建并返回一个以该字符串参数为名称的 Symbol 值，并登记在全局环境中供搜索。

~~~javascript
let yellow = Symbol("Yellow");
let yellow1 = Symbol.for("Yellow");
yellow === yellow1;      // false
 
let yellow2 = Symbol.for("Yellow");
yellow1 === yellow2;     // true
~~~

**Symbol.keyFor()**

Symbol.keyFor() 返回一个已登记的 Symbol 类型值的 key ，用来检测该字符串参数作为名称的 Symbol 值是否已被登记。

~~~JavaScript
let yellow1 = Symbol.for("Yellow");
Symbol.keyFor(yellow1);    // "Yellow"
~~~

### Map与Set

####**Map对象**

Map 对象保存键值对。任何值(对象或者原始值) 都可以作为一个键或一个值

与Object的区别

+ 一个 Object 的键只能是字符串或者 Symbols，但一个 Map 的键可以是任意值。
+ Map 中的键值是有序的（FIFO 原则），而添加到对象中的键则不是。
+ Map 的键值对个数可以从 size 属性获取，而 Object 的键值对个数只能手动计算。
+ Object 都有自己的原型，原型链上的键名有可能和你自己在对象上的设置的键名产生冲突。

**Map 中的 key**

字符串

~~~JavaScript
var myMap = new Map();
var keyString = "a string"; 
 
myMap.set(keyString, "和键'a string'关联的值");
 
myMap.get(keyString);    // "和键'a string'关联的值"
myMap.get("a string");   // "和键'a string'关联的值"
                         // 因为 keyString === 'a string
~~~

对象

~~~JavaScript
var myMap = new Map();
var keyObj = {}, 
 
myMap.set(keyObj, "和键 keyObj 关联的值");

myMap.get(keyObj); // "和键 keyObj 关联的值"
myMap.get({}); // undefined, 因为 keyObj !== {}
~~~

函数

~~~JavaScript
var myMap = new Map();
var keyFunc = function () {}, // 函数
 
myMap.set(keyFunc, "和键 keyFunc 关联的值");
 
myMap.get(keyFunc); // "和键 keyFunc 关联的值"
myMap.get(function() {}) // undefined, 因为 keyFunc !== function () {}
~~~

**Map的迭代**

对Map进行遍历可以用到以下的语句和函数

**for……of**

~~~JavaScript
var myMap = new Map();
myMap.set(0, "zero");
myMap.set(1, "one");
 
// 将会显示两个 log。 一个是 "0 = zero" 另一个是 "1 = one"
for (var [key, value] of myMap) {
  console.log(key + " = " + value);
}
for (var [key, value] of myMap.entries()) {
  console.log(key + " = " + value);
}
/* 这个 entries 方法返回一个新的 Iterator 对象，它按插入顺序包含了 Map 对象中每个元素的 [key, value] 数组。 */
 
// 将会显示两个log。 一个是 "0" 另一个是 "1"
for (var key of myMap.keys()) {
  console.log(key);
}
/* 这个 keys 方法返回一个新的 Iterator 对象， 它按插入顺序包含了 Map 对象中每个元素的键。 */
 
// 将会显示两个log。 一个是 "zero" 另一个是 "one"
for (var value of myMap.values()) {
  console.log(value);
}
/* 这个 values 方法返回一个新的 Iterator 对象，它按插入顺序包含了 Map 对象中每个元素的值。 */
~~~

**forEach（）函数**

~~~JavaScript
var myMap = new Map();
myMap.set(0, "zero");
myMap.set(1, "one");
 
// 将会显示两个 logs。 一个是 "0 = zero" 另一个是 "1 = one"
myMap.forEach(function(value, key) {
  console.log(key + " = " + value);
}, myMap)
~~~

对Map对象的一些常规操作

**Map和Array的转换**

~~~JavaScript
var kvArray = [["key1", "value1"], ["key2", "value2"]];
 
// Map 构造函数可以将一个 二维 键值对数组转换成一个 Map 对象
var myMap = new Map(kvArray);
//相当于进行了
//myMap.set("key1", "value1");
//myMap.set("key2", "value2");
//的操作 

// 使用 Array.from 函数可以将一个 Map 对象转换成一个二维键值对数组
var outArray = Array.from(myMap);
~~~

**Map的克隆**

~~~JavaScript
var myMap1 = new Map([["key1", "value1"], ["key2", "value2"]]);
var myMap2 = new Map(myMap1);
 
console.log(original === clone); 
// 打印 false。 Map 对象构造函数生成实例，迭代出新的对象
~~~

**Map的合并**

形式：

**new Map([...first, ...second]);**

~~~JavaScript
var first = new Map([[1, 'one'], [2, 'two'], [3, 'three'],]);
var second = new Map([[1, 'uno'], [2, 'dos']]);
 
// 合并两个 Map 对象时，如果有重复的键值，则后面的会覆盖前面的，对应值即 uno，dos， three
var merged = new Map([...first, ...second]);
~~~

---

#### Set对象

Set 对象允许你存储任何类型的唯一值，无论是原始值或者是对象引用。

~~~JavaScript
let mySet = new Set();
 
mySet.add(1); // Set(1) {1}
mySet.add(5); // Set(2) {1, 5}
mySet.add(5); // Set(2) {1, 5} 这里体现了值的唯一性
mySet.add("some text"); 
// Set(3) {1, 5, "some text"} 这里体现了类型的多样性
var o = {a: 1, b: 2}; 
mySet.add(o);
mySet.add({a: 1, b: 2}); 
// Set(5) {1, 5, "some text", {…}, {…}} 
// 这里体现了对象之间引用不同不恒等，即使值相同，Set 也能存储
~~~

需要注意的是

+ +0 与 -0 在存储判断唯一性的时候是恒等的，所以不能重复；
+ undefined 与 undefined 是恒等的，所以不能重复；
+ NaN 与 NaN 是不恒等的，但是在 Set 中只能存一个，不能重复。

**类型转换**

数组

~~~JavaScript
// Array 转 Set
var mySet = new Set(["value1", "value2", "value3"]);
// 用...操作符，将 Set 转 Array
var myArray = [...mySet];
String
// String 转 Set
var mySet = new Set('hello');  // Set(4) {"h", "e", "l", "o"}
// 注：Set 中 toString 方法是不能将 Set 转换成 String的
~~~

**Set 对象作用（利用Set对象只能存不重复的值的特性）**

数组去重

~~~JavaScript
var mySet = new Set([1, 2, 3, 4, 4]);
[...mySet]; // [1, 2, 3, 4]
~~~

并集

~~~javascript
var a = new Set([1, 2, 3]);
var b = new Set([4, 3, 2]);
var union = new Set([...a, ...b]); // {1, 2, 3, 4}
~~~

**交集**

~~~JavaScript
var a = new Set([1, 2, 3]);
var b = new Set([4, 3, 2]);
var intersect = new Set([...a].filter(x => b.has(x))); // {2, 3}
~~~

**差集**

~~~JavaScript
var a = new Set([1, 2, 3]);
var b = new Set([4, 3, 2]);
var difference = new Set([...a].filter(x => !b.has(x))); // {1}
~~~

---

###字符串

**在Es6中拓展了一些新方法**

ES6 之前**判断字符串是否包含子串**，用 indexOf 方法，ES6 新增了子串的识别方法。

+ **includes()**：返回布尔值，判断是否找到参数字符串。
+ **startsWith()**：返回布尔值，判断参数字符串是否在原字符串的头部。
+ **endsWith()**：返回布尔值，判断参数字符串是否在原字符串的尾部。

~~~JavaScript
let string = "apple,banana,orange";
string.includes("banana");     // true
string.startsWith("apple");    // true
string.endsWith("apple");      // false
string.startsWith("banana",6)  // true
~~~

如果想要知道子串的位置还是要用  indexOf 和 lastIndexOf 。

**字符串重复**

repeat()：返回新的字符串，表示将字符串重复指定次数返回。

~~~JavaScript
console.log("Hello,".repeat(2));  // "Hello,Hello,"
~~~

+ 如果参数是小数，向下取整
+ 如果参数是 0 至 -1 之间的小数，会进行取整运算，0 至 -1 之间的小数取整得到 -0 ，等同于 repeat 零次
+ 如果参数是 NaN，等同于 repeat 零次
+ 如果参数是负数或者 Infinity ，会报错:
+ 如果传入的参数是字符串，则会先将字符串转化为数字

**字符串补全**

+ **padStart**：返回新的字符串，表示用参数字符串从头部（左侧）补全原字符串。
+ **padEnd**：返回新的字符串，表示用参数字符串从尾部（右侧）补全原字符串。

以上两个方法接受两个参数，第一个参数是指定生成的字符串的最小长度，第二个参数是用来补全的字符串。如果没有指定第二个参数，默认用空格填充。

~~~JavaScript
console.log("h".padStart(5,"o"));  // "ooooh"
console.log("h".padEnd(5,"o"));    // "hoooo"
console.log("h".padStart(5));      // "    h"
~~~

+ 如果指定的长度小于或者等于原字符串的长度，则返回原字符串:
+ 如果原字符串加上补全字符串长度大于指定长度，则截去超出位数的补全字符串:
+ 常用于补全位数：

~~~JavaScript
console.log("123".padStart(10,"0"));  // "0000000123"
~~~

**模板字符串**

模板字符串相当于加强版的字符串，用反引号 **`**,除了作为普通字符串，还可以用来定义多行字符串，还可以在字符串中加入变量和表达式。