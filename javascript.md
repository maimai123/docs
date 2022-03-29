# JavaScript Standard Style

[![js-standard-style](./images/standard.svg)](https://github.com/standard/standard)

这是 JavaScript [standard](https://github.com/standard/standard) 代码规范的全文。

掌握本规范的最好方法是安装并在自己的代码中使用它。

## 细则

- **使用两个空格**进行缩进。

  eslint: [`indent`](http://eslint.org/docs/rules/indent)

  ```js
  function hello(name) {
    console.log('hi', name)
  }
  ```

- 除需要转义的情况外，**字符串统一使用单引号**。

  eslint: [`quotes`](http://eslint.org/docs/rules/quotes)

  ```js
  console.log('hello there')
  $("<div class='box'>")
  ```

- **不要定义未使用的变量**。

  eslint: [`no-unused-vars`](http://eslint.org/docs/rules/no-unused-vars)

  ```js
  function myFunction() {
    var result = something() // ✗ avoid
  }
  ```

- **关键字后面加空格**。

  eslint: [`keyword-spacing`](http://eslint.org/docs/rules/keyword-spacing)

  ```js
  if (condition) { ... }   // ✓ ok
  if(condition) { ... }    // ✗ avoid
  ```

- **函数声明时括号与函数名间加空格**。

  eslint: [`space-before-function-paren`](http://eslint.org/docs/rules/space-before-function-paren)

  ```js
  function name (arg) { ... }   // ✓ ok
  function name(arg) { ... }    // ✗ avoid

  run(function () { ... })      // ✓ ok
  run(function() { ... })       // ✗ avoid
  ```

- **始终使用** `===` 替代 `==`。<br>
  例外： `obj == null` 可以用来检查 `null || undefined`。

  eslint: [`eqeqeq`](http://eslint.org/docs/rules/eqeqeq)

  ```js
  if (name === 'John')   // ✓ ok
  if (name == 'John')    // ✗ avoid
  ```

  ```js
  if (name !== 'John')   // ✓ ok
  if (name != 'John')    // ✗ avoid
  ```

- **字符串拼接操作符 (Infix operators)** 之间要留空格。

  eslint: [`space-infix-ops`](http://eslint.org/docs/rules/space-infix-ops)

  ```js
  // ✓ ok
  var x = 2
  var message = 'hello, ' + name + '!'
  ```

  ```js
  // ✗ avoid
  var x = 2
  var message = 'hello, '+name+'!'
  ```

- **逗号后面加空格**。

  eslint: [`comma-spacing`](http://eslint.org/docs/rules/comma-spacing)

  ```js
  // ✓ ok
  var list = [1, 2, 3, 4]
  function greet (name, options) { ... }
  ```

  ```js
  // ✗ avoid
  var list = [1,2,3,4]
  function greet (name,options) { ... }
  ```

- **else 关键字要与花括号**保持在同一行。

  eslint: [`brace-style`](http://eslint.org/docs/rules/brace-style)

  ```js
  // ✓ ok
  if (condition) {
    // ...
  } else {
    // ...
  }
  ```

  ```js
  // ✗ avoid
  if (condition) {
    // ...
  }
  else {
    // ...
  }
  ```

- **多行 if 语句的**的括号不能省。

  eslint: [`curly`](http://eslint.org/docs/rules/curly)

  ```js
  // ✓ ok
  if (options.quiet !== true) console.log('done')
  ```

  ```js
  // ✓ ok
  if (options.quiet !== true) {
    console.log('done')
  }
  ```

  ```js
  // ✗ avoid
  if (options.quiet !== true)
  console.log('done')
  ```

- **不要丢掉**异常处理中`err`参数。

  eslint: [`handle-callback-err`](http://eslint.org/docs/rules/handle-callback-err)

  ```js
  // ✓ ok
  run(function(err) {
    if (err) throw err
    window.alert('done')
  })
  ```

  ```js
  // ✗ avoid
  run(function(err) {
    window.alert('done')
  })
  ```

- **不允许有连续多行空行**。

  eslint: [`no-multiple-empty-lines`](http://eslint.org/docs/rules/no-multiple-empty-lines)

  ```js
  // ✓ ok
  var value = 'hello world'
  console.log(value)
  ```

  ```js
  // ✗ avoid
  var value =     'hello world'
  ```

console.log(value)

````

* **对于三元运算符** `?` 和 `:` 与他们所负责的代码处于同一行

eslint: [`operator-linebreak`](http://eslint.org/docs/rules/operator-linebreak)

```js
// ✓ ok
var location = env.development ? 'localhost' : 'www.api.com'

// ✓ ok
var location = env.development
  ? 'localhost'
  : 'www.api.com'

// ✗ avoid
var location = env.development ?
  'localhost' :
  'www.api.com'
````

- **每个 var 关键字**单独声明一个变量。

  eslint: [`one-var`](http://eslint.org/docs/rules/one-var)

  ```js
  // ✓ ok
  var silent = true
  var verbose = true

  // ✗ avoid
  var silent = true,
    verbose = true

  ```

- **条件语句中赋值语句**使用括号包起来。这样使得代码更加清晰可读，而不会认为是将条件判断语句的全等号（`===`）错写成了等号（`=`）。

  eslint: [`no-cond-assign`](http://eslint.org/docs/rules/no-cond-assign)

  ```js
  // ✓ ok
  while ((m = text.match(expr))) {
    // ...
  }

  // ✗ avoid
  while (m = text.match(expr)) {
    // ...
  }
  ```

- **单行代码块两边加空格**。

  eslint: [`block-spacing`](http://eslint.org/docs/rules/block-spacing)

  ```js
  function foo() {
    return true
  } // ✗ avoid
  function foo() {
    return true
  } // ✓ ok
  ```

- **对于变量和函数名统一使用驼峰命名法**。

  eslint: [`camelcase`](http://eslint.org/docs/rules/camelcase)

  ```js
  function my_function() {} // ✗ avoid
  function myFunction() {} // ✓ ok

  var my_var = 'hello' // ✗ avoid
  var myVar = 'hello' // ✓ ok
  ```

- **始终将逗号置于行末**。

  eslint: [`comma-style`](http://eslint.org/docs/rules/comma-style)

  ```js
  var obj = {
    foo: 'foo',
    bar: 'bar' // ✗ avoid
  }

  var obj = {
    foo: 'foo',
    bar: 'bar', // ✓ ok
  }
  ```

- **文件末尾留一空行**。

  eslint: [`eol-last`](http://eslint.org/docs/rules/eol-last)


- **键值对当中冒号与值之间要留空白**。

  eslint: [`key-spacing`](http://eslint.org/docs/rules/key-spacing)

  ```js
  var obj = { key:'value' } // ✗ avoid
  var obj = { key: 'value' } // ✓ ok
  ```

- **构造函数要以大写字母开头**。

  eslint: [`new-cap`](http://eslint.org/docs/rules/new-cap)

  ```js
  function animal() {}
  var dog = new animal() // ✗ avoid

  function Animal() {}
  var dog = new Animal() // ✓ ok
  ```

- **对象中定义了存值器，一定要对应的定义取值器**。

  eslint: [`accessor-pairs`](http://eslint.org/docs/rules/accessor-pairs)

  ```js
  var person = {
    set name(value) {
      // ✗ avoid
      this._name = value
    }
  }

  var person = {
    set name(value) {
      this._name = value
    },
    get name() {
      // ✓ ok
      return this._name
    }
  }
  ```

- **子类的构造器中一定要调用 `super`**

  eslint: [`constructor-super`](http://eslint.org/docs/rules/constructor-super)

  ```js
  class Dog {
    constructor() { // ✗ avoid
    }
  }

  class Dog extends Mammal {
    constructor() {
      super() // ✓ ok
    }
  }
  ```

- **使用数组字面量而不是构造器**。

  eslint: [`no-array-constructor`](http://eslint.org/docs/rules/no-array-constructor)

  ```js
  var nums = new Array(1, 2, 3) // ✗ avoid
  var nums = [1, 2, 3] // ✓ ok
  ```

- **避免使用 `arguments.callee` 和 `arguments.caller`**。

  eslint: [`no-caller`](http://eslint.org/docs/rules/no-caller)

  ```js
  function foo(n) {
    if (n <= 0) return

    arguments.callee(n - 1) // ✗ avoid
  }

  function foo(n) {
    if (n <= 0) return

    foo(n - 1)
  }
  ```

- **避免对类名重新赋值**。

  eslint: [`no-class-assign`](http://eslint.org/docs/rules/no-class-assign)

  ```js
  class Dog {}
  Dog = 'Fido' // ✗ avoid
  ```

- **避免修改使用 `const` 声明的变量**。

  eslint: [`no-const-assign`](http://eslint.org/docs/rules/no-const-assign)

  ```js
  const score = 100
  score = 125 // ✗ avoid
  ```

- **避免使用常量作为条件表达式的条件（循环语句除外）**。

  eslint: [`no-constant-condition`](http://eslint.org/docs/rules/no-constant-condition)

  ```js
  if (false) {
    // ✗ avoid
    // ...
  }

  if (x === 0) {
    // ✓ ok
    // ...
  }

  while (true) {
    // ✓ ok
    // ...
  }
  ```

- **不要使用 `debugger`**。

  eslint: [`no-debugger`](http://eslint.org/docs/rules/no-debugger)

  ```js
  function sum(a, b) {
    debugger // ✗ avoid
    return a + b
  }
  ```

- **不要对变量使用 `delete` 操作**。

  eslint: [`no-delete-var`](http://eslint.org/docs/rules/no-delete-var)

  ```js
  var name
  delete name // ✗ avoid
  name = null // ✓ ok
  ```

- **不要定义冗余的函数参数**。

  eslint: [`no-dupe-args`](http://eslint.org/docs/rules/no-dupe-args)

  ```js
  function sum(a, b, a) {
    // ✗ avoid
    // ...
  }

  function sum(a, b, c) {
    // ✓ ok
    // ...
  }
  ```

- **类中不要定义冗余的属性**。

  eslint: [`no-dupe-class-members`](http://eslint.org/docs/rules/no-dupe-class-members)

  ```js
  class Dog {
    bark() {}
    bark() {} // ✗ avoid
  }
  ```

- **对象字面量中不要定义重复的属性**。

  eslint: [`no-dupe-keys`](http://eslint.org/docs/rules/no-dupe-keys)

  ```js
  var user = {
    name: 'Jane Doe',
    name: 'John Doe' // ✗ avoid
  }
  ```

- **`switch` 语句中不要定义重复的 `case` 分支**。

  eslint: [`no-duplicate-case`](http://eslint.org/docs/rules/no-duplicate-case)

  ```js
  switch (id) {
    case 1:
    // ...
    case 1: // ✗ avoid
  }
  ```

- **同一模块有多个导入时一次性写完**。

  eslint: [`no-duplicate-imports`](http://eslint.org/docs/rules/no-duplicate-imports)

  ```js
  import { myFunc1 } from 'module'
  import { myFunc2 } from 'module' // ✗ avoid

  import { myFunc1, myFunc2 } from 'module' // ✓ ok
  ```

- **正则中不要使用空字符**。

  eslint: [`no-empty-character-class`](http://eslint.org/docs/rules/no-empty-character-class)

  ```js
  const myRegex = /^abc[]/ // ✗ avoid
  const myRegex = /^abc[a-z]/ // ✓ ok
  ```

- **不要解构空值**。

  eslint: [`no-empty-pattern`](http://eslint.org/docs/rules/no-empty-pattern)

  ```js
  const {
    a: {}
  } = foo // ✗ avoid
  const {
    a: { b }
  } = foo // ✓ ok
  ```

- **不要使用 `eval()`**。

  eslint: [`no-eval`](http://eslint.org/docs/rules/no-eval)

  ```js
  eval('var result = user.' + propName) // ✗ avoid
  var result = user[propName] // ✓ ok
  ```

- **`catch` 中不要对错误重新赋值**。

  eslint: [`no-ex-assign`](http://eslint.org/docs/rules/no-ex-assign)

  ```js
  try {
    // ...
  } catch (e) {
    e = 'new value' // ✗ avoid
  }

  try {
    // ...
  } catch (e) {
    const newVal = 'new value' // ✓ ok
  }
  ```

- **避免多余的函数上下文绑定**。

  eslint: [`no-extra-bind`](http://eslint.org/docs/rules/no-extra-bind)

  ```js
  const name = function() {
    getName()
  }.bind(user) // ✗ avoid

  const name = function() {
    this.getName()
  }.bind(user) // ✓ ok
  ```

- **避免不必要的布尔转换**。

  eslint: [`no-extra-boolean-cast`](http://eslint.org/docs/rules/no-extra-boolean-cast)

  ```js
  const result = true
  if (!!result) {
    // ✗ avoid
    // ...
  }

  const result = true
  if (result) {
    // ✓ ok
    // ...
  }
  ```


- **`switch` 一定要使用 `break` 来将条件分支正常中断**。

  eslint: [`no-fallthrough`](http://eslint.org/docs/rules/no-fallthrough)

  ```js
  switch (filter) {
    case 1:
      doSomething() // ✗ avoid
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
      doSomething()
      break // ✓ ok
    case 2:
      doSomethingElse()
  }

  switch (filter) {
    case 1:
      doSomething()
    // fallthrough  // ✓ ok
    case 2:
      doSomethingElse()
  }
  ```

- **不要省去小数点前面的 0**。

  eslint: [`no-floating-decimal`](http://eslint.org/docs/rules/no-floating-decimal)

  ```js
  const discount = 0.5 // ✗ avoid
  const discount = 0.5 // ✓ ok
  ```

- **避免对声明过的函数重新赋值**。

  eslint: [`no-func-assign`](http://eslint.org/docs/rules/no-func-assign)

  ```js
  function myFunc() {}
  myFunc = myOtherFunc // ✗ avoid
  ```

- **不要对全局只读对象重新赋值**。

  eslint: [`no-global-assign`](http://eslint.org/docs/rules/no-global-assign)

  ```js
  window = {} // ✗ avoid
  ```

- **注意隐式的 `eval()`**。

  eslint: [`no-implied-eval`](http://eslint.org/docs/rules/no-implied-eval)

  ```js
  setTimeout("alert('Hello world')") // ✗ avoid
  setTimeout(function() {
    alert('Hello world')
  }) // ✓ ok
  ```

- **嵌套的代码块中禁止再定义函数**。

  eslint: [`no-inner-declarations`](http://eslint.org/docs/rules/no-inner-declarations)

  ```js
  if (authenticated) {
    function setAuthUser() {} // ✗ avoid
  }
  ```

- **不要向 `RegExp` 构造器传入非法的正则表达式**。

  eslint: [`no-invalid-regexp`](http://eslint.org/docs/rules/no-invalid-regexp)

  ```js
  RegExp('[a-z') // ✗ avoid
  RegExp('[a-z]') // ✓ ok
  ```

- **不要使用非法的空白符**。

  eslint: [`no-irregular-whitespace`](http://eslint.org/docs/rules/no-irregular-whitespace)

  ```js
  function myFunc() /*<NBSP>*/ {} // ✗ avoid
  ```

- **禁止使用 `__iterator__`**。

  eslint: [`no-iterator`](http://eslint.org/docs/rules/no-iterator)

  ```js
  Foo.prototype.__iterator__ = function() {} // ✗ avoid
  ```

- **外部变量不要与对象属性重名**。

  eslint: [`no-label-var`](http://eslint.org/docs/rules/no-label-var)

  ```js
  var score = 100
  function game() {
    score: while (true) {
      // ✗ avoid
      score -= 10
      if (score > 0) continue score
      break
    }
  }
  ```

- **不要使用标签语句**。

  eslint: [`no-labels`](http://eslint.org/docs/rules/no-labels)

  ```js
  label: while (true) {
    break label // ✗ avoid
  }
  ```

- **不要书写不必要的嵌套代码块**。

  eslint: [`no-lone-blocks`](http://eslint.org/docs/rules/no-lone-blocks)

  ```js
  function myFunc() {
    {
      // ✗ avoid
      myOtherFunc()
    }
  }

  function myFunc() {
    myOtherFunc() // ✓ ok
  }
  ```

- **不要混合使用空格与制表符作为缩进**。

  eslint: [`no-mixed-spaces-and-tabs`](http://eslint.org/docs/rules/no-mixed-spaces-and-tabs)

- **除了缩进，不要使用多个空格**。

  eslint: [`no-multi-spaces`](http://eslint.org/docs/rules/no-multi-spaces)

  ```js
  const id = 1234 // ✗ avoid
  const id = 1234 // ✓ ok
  ```

- **不要使用多行字符串**。

  eslint: [`no-multi-str`](http://eslint.org/docs/rules/no-multi-str)

  ```js
  const message =
    'Hello \
                   world' // ✗ avoid
  ```

- **`new` 创建对象实例后需要赋值给变量**。

  eslint: [`no-new`](http://eslint.org/docs/rules/no-new)

  ```js
  new Character() // ✗ avoid
  const character = new Character() // ✓ ok
  ```

- **禁止使用 `Function` 构造器**。

  eslint: [`no-new-func`](http://eslint.org/docs/rules/no-new-func)

  ```js
  var sum = new Function('a', 'b', 'return a + b') // ✗ avoid
  ```

- **禁止使用 `Object` 构造器**。

  eslint: [`no-new-object`](http://eslint.org/docs/rules/no-new-object)

  ```js
  let config = new Object() // ✗ avoid
  ```

- **禁止使用 `new require`**。

  eslint: [`no-new-require`](http://eslint.org/docs/rules/no-new-require)

  ```js
  const myModule = new require('my-module') // ✗ avoid
  ```


- **禁止使用原始包装器**。

  eslint: [`no-new-wrappers`](http://eslint.org/docs/rules/no-new-wrappers)

  ```js
  const message = new String('hello') // ✗ avoid
  ```

- **不要将全局对象的属性作为函数调用**。

  eslint: [`no-obj-calls`](http://eslint.org/docs/rules/no-obj-calls)

  ```js
  const math = Math() // ✗ avoid
  ```

- **不要使用八进制字面量**。

  eslint: [`no-octal`](http://eslint.org/docs/rules/no-octal)

  ```js
  const num = 042 // ✗ avoid
  const num = '042' // ✓ ok
  ```

- **字符串字面量中也不要使用八进制转义字符**。

  eslint: [`no-octal-escape`](http://eslint.org/docs/rules/no-octal-escape)

  ```js
  const copyright = 'Copyright \251' // ✗ avoid
  ```

- **使用 `__dirname` 和 `__filename` 时尽量避免使用字符串拼接**。

  eslint: [`no-path-concat`](http://eslint.org/docs/rules/no-path-concat)

  ```js
  const pathToFile = __dirname + '/app.js' // ✗ avoid
  const pathToFile = path.join(__dirname, 'app.js') // ✓ ok
  ```

- 使用 `getPrototypeOf` 来替代 **`__proto__`**。

  eslint: [`no-proto`](http://eslint.org/docs/rules/no-proto)

  ```js
  const foo = obj.__proto__ // ✗ avoid
  const foo = Object.getPrototypeOf(obj) // ✓ ok
  ```

- **不要重复声明变量**。

  eslint: [`no-redeclare`](http://eslint.org/docs/rules/no-redeclare)

  ```js
  let name = 'John'
  let name = 'Jane' // ✗ avoid

  let name = 'John'
  name = 'Jane' // ✓ ok
  ```

- **正则中避免使用多个空格**。

  eslint: [`no-regex-spaces`](http://eslint.org/docs/rules/no-regex-spaces)

  ```js
  const regexp = /test   value/ // ✗ avoid

  const regexp = /test {3}value/ // ✓ ok
  const regexp = /test value/ // ✓ ok
  ```

- **return 语句中的赋值必需有括号包裹**。

  eslint: [`no-return-assign`](http://eslint.org/docs/rules/no-return-assign)

  ```js
  function sum(a, b) {
    return result = a + b // ✗ avoid
  }

  function sum(a, b) {
    return (result = a + b) // ✓ ok
  }
  ```

- **避免将变量赋值给自己**。

  eslint: [`no-self-assign`](http://eslint.org/docs/rules/no-self-assign)

  ```js
  name = name // ✗ avoid
  ```

- **避免将变量与自己进行比较操作**。

  esint: [`no-self-compare`](http://eslint.org/docs/rules/no-self-compare)

  ```js
  if (score === score) {
  } // ✗ avoid
  ```

- **避免使用逗号操作符**。

  eslint: [`no-sequences`](http://eslint.org/docs/rules/no-sequences)

  ```js
  if ((doSomething(), !!test)) {
  } // ✗ avoid
  ```

- **不要随意更改关键字的值**。

  eslint: [`no-shadow-restricted-names`](http://eslint.org/docs/rules/no-shadow-restricted-names)

  ```js
  let undefined = 'value' // ✗ avoid
  ```

- **禁止使用稀疏数组（Sparse arrays）**。

  eslint: [`no-sparse-arrays`](http://eslint.org/docs/rules/no-sparse-arrays)

  ```js
  let fruits = ['apple', , 'orange'] // ✗ avoid
  ```

- **不要使用制表符**。

  eslint: [`no-tabs`](http://eslint.org/docs/rules/no-tabs)

- **正确使用 ES6 中的字符串模板**。

  eslint: [`no-template-curly-in-string`](http://eslint.org/docs/rules/no-template-curly-in-string)

  ```js
  const message = 'Hello ${name}' // ✗ avoid
  const message = `Hello ${name}` // ✓ ok
  ```

- **使用 `this` 前请确保 `super()` 已调用**。

  eslint: [`no-this-before-super`](http://eslint.org/docs/rules/no-this-before-super)

  ```js
  class Dog extends Animal {
    constructor() {
      this.legs = 4 // ✗ avoid
      super()
    }
  }
  ```

- **用 `throw` 抛错时，抛出 `Error` 对象而不是字符串**。

  eslint: [`no-throw-literal`](http://eslint.org/docs/rules/no-throw-literal)

  ```js
  throw 'error' // ✗ avoid
  throw new Error('error') // ✓ ok
  ```

- **行末不留空格**。

  eslint: [`no-trailing-spaces`](http://eslint.org/docs/rules/no-trailing-spaces)

- **不要使用 `undefined` 来初始化变量**。

  eslint: [`no-undef-init`](http://eslint.org/docs/rules/no-undef-init)

  ```js
  let name = undefined // ✗ avoid

  let name
  name = 'value' // ✓ ok
  ```

- **循环语句中注意更新循环变量**。

  eslint: [`no-unmodified-loop-condition`](http://eslint.org/docs/rules/no-unmodified-loop-condition)

  ```js
  for (let i = 0; i < items.length; j++) {...}    // ✗ avoid
  for (let i = 0; i < items.length; i++) {...}    // ✓ ok
  ```

- **如果有更好的实现，尽量不要使用三元表达式**。

  eslint: [`no-unneeded-ternary`](http://eslint.org/docs/rules/no-unneeded-ternary)

  ```js
  let score = val ? val : 0 // ✗ avoid
  let score = val || 0 // ✓ ok
  ```

- **`return`，`throw`，`continue` 和 `break` 后不要再跟代码**。

  eslint: [`no-unreachable`](http://eslint.org/docs/rules/no-unreachable)

  ```js
  function doSomething() {
    return true
    console.log('never called') // ✗ avoid
  }
  ```

- **`finally` 代码块中不要再改变程序执行流程**。

  eslint: [`no-unsafe-finally`](http://eslint.org/docs/rules/no-unsafe-finally)

  ```js
  try {
    // ...
  } catch (e) {
    // ...
  } finally {
    return 42 // ✗ avoid
  }
  ```

- **关系运算符的左值不要做取反操作**。

  eslint: [`no-unsafe-negation`](http://eslint.org/docs/rules/no-unsafe-negation)

  ```js
  if (!key in obj) {
  } // ✗ avoid
  ```

- **避免不必要的 `.call()` 和 `.apply()`**。

  eslint: [`no-useless-call`](http://eslint.org/docs/rules/no-useless-call)

  ```js
  sum.call(null, 1, 2, 3) // ✗ avoid
  ```

- **避免使用不必要的计算值作对象属性**。

  eslint: [`no-useless-computed-key`](http://eslint.org/docs/rules/no-useless-computed-key)

  ```js
  const user = { ['name']: 'John Doe' } // ✗ avoid
  const user = { name: 'John Doe' } // ✓ ok
  ```

- **禁止多余的构造器**。

  eslint: [`no-useless-constructor`](http://eslint.org/docs/rules/no-useless-constructor)

  ```js
  class Car {
    constructor() {
      // ✗ avoid
    }
  }
  ```

- **禁止不必要的转义**。

  eslint: [`no-useless-escape`](http://eslint.org/docs/rules/no-useless-escape)


- **import, export 和解构操作中，禁止赋值到同名变量**。

  eslint: [`no-useless-rename`](http://eslint.org/docs/rules/no-useless-rename)


- **属性前面不要加空格**。

  eslint: [`no-whitespace-before-property`](http://eslint.org/docs/rules/no-whitespace-before-property)


- **禁止使用 `with`**。

  eslint: [`no-with`](http://eslint.org/docs/rules/no-with)

  ```js
  with (val) {...}    // ✗ avoid
  ```

- **对象属性换行时注意统一代码风格**。

  eslint: [`object-property-newline`](http://eslint.org/docs/rules/object-property-newline)

  ```js
  const user = {
    name: 'Jane Doe', age: 30,
    username: 'jdoe86' // ✗ avoid
  }

  const user = { name: 'Jane Doe', age: 30, username: 'jdoe86' } // ✓ ok

  const user = {
    name: 'Jane Doe',
    age: 30,
    username: 'jdoe86',
  } // ✓ ok
  ```

- **代码块中避免多余留白**。

  eslint: [`padded-blocks`](http://eslint.org/docs/rules/padded-blocks)

  ```js
  if (user) {
    // ✗ avoid
    const name = getName()
  }

  if (user) {
    const name = getName() // ✓ ok
  }
  ```

- **展开运算符与它的表达式间不要留空白**。

  eslint: [`rest-spread-spacing`](http://eslint.org/docs/rules/rest-spread-spacing)


- **遇到分号时空格要后留前不留**。

  eslint: [`semi-spacing`](http://eslint.org/docs/rules/semi-spacing)

  ```js
  for (let i = 0 ;i < items.length ;i++) {...}    // ✗ avoid
  for (let i = 0; i < items.length; i++) {...}    // ✓ ok
  ```

- **代码块首尾留空格**。

  eslint: [`space-before-blocks`](http://eslint.org/docs/rules/space-before-blocks)

  ```js
  if (admin){...}     // ✗ avoid
  if (admin) {...}    // ✓ ok
  ```

- **圆括号间不留空格**。

  eslint: [`space-in-parens`](http://eslint.org/docs/rules/space-in-parens)

  ```js
  getName( name ) // ✗ avoid
  getName(name) // ✓ ok
  ```

- **一元运算符后面跟一个空格**。

  eslint: [`space-unary-ops`](http://eslint.org/docs/rules/space-unary-ops)


- **注释首尾留空格**。

  eslint: [`spaced-comment`](http://eslint.org/docs/rules/spaced-comment)

  ```js
  //comment           // ✗ avoid
  // comment          // ✓ ok

  /*comment*/ // ✗ avoid
  /* comment */ // ✓ ok
  ```

- **模板字符串中变量前后不加空格**。

  eslint: [`template-curly-spacing`](http://eslint.org/docs/rules/template-curly-spacing)

  ```js
  const message = `Hello, ${ name }` // ✗ avoid
  const message = `Hello, ${name}` // ✓ ok
  ```

- **检查 `NaN` 的正确姿势是使用 `isNaN()`**。

  eslint: [`use-isnan`](http://eslint.org/docs/rules/use-isnan)

  ```js
  if (price === NaN) {
  } // ✗ avoid
  if (isNaN(price)) {
  } // ✓ ok
  ```

- **用合法的字符串跟 `typeof` 进行比较操作**。

  eslint: [`valid-typeof`](http://eslint.org/docs/rules/valid-typeof)

  ```js
  typeof name === 'undefimed' // ✗ avoid
  typeof name === 'undefined' // ✓ ok
  ```

- **自调用匿名函数 (IIFEs) 使用括号包裹**。

  eslint: [`wrap-iife`](http://eslint.org/docs/rules/wrap-iife)

  ```js
  const getName = (function() {})() // ✓ ok
  ```

- **`yield *` 中的 `*` 前后都要有空格**。

  eslint: [`yield-star-spacing`](http://eslint.org/docs/rules/yield-star-spacing)

  ```js
  yield* increment() // ✗ avoid
  yield * increment() // ✓ ok
  ```

- **请书写优雅的条件语句（avoid Yoda conditions）**。

  eslint: [`yoda`](http://eslint.org/docs/rules/yoda)

  ```js
  if (42 === age) {
  } // ✗ avoid
  if (age === 42) {
  } // ✓ ok
  ```



## 风格
方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式。

正例： `localValue / getHttpMessage() / inputUserId`

\***\*其中 method 方法命名必须是 动词 或者 动词+名词 形式\*\***

正例：`saveShopCarData /openShopCarInfoDialog`

反例：`save / open / show / go`

\***\*特此说明，增删查改，详情统一使用如下 5 个单词，不得使用其他（目的是为了统一各个端）\*\***

`add / update / delete / detail / get`

**附： 函数方法常用的动词:**

```js
get 获取/set 设置,
add 增加/remove 删除
create 创建/destory 移除
start 启动/stop 停止
open 打开/close 关闭,
read 读取/write 写入
load 载入/save 保存,
create 创建/destroy 销毁
begin 开始/end 结束,
backup 备份/restore 恢复
import 导入/export 导出,
split 分割/merge 合并
inject 注入/extract 提取,
attach 附着/detach 脱离
bind 绑定/separate 分离,
view 查看/browse 浏览
edit 编辑/modify 修改,
select 选取/mark 标记
copy 复制/paste 粘贴,
undo 撤销/redo 重做
insert 插入/delete 移除,
add 加入/append 添加
clean 清理/clear 清除,
index 索引/sort 排序
find 查找/search 搜索,
increase 增加/decrease 减少
play 播放/pause 暂停,
launch 启动/run 运行
compile 编译/execute 执行,
debug 调试/trace 跟踪
observe 观察/listen 监听,
build 构建/publish 发布
input 输入/output 输出,
encode 编码/decode 解码
encrypt 加密/decrypt 解密,
compress 压缩/decompress 解压缩
pack 打包/unpack 解包,
parse 解析/emit 生成
connect 连接/disconnect 断开,
send 发送/receive 接收
download 下载/upload 上传,
refresh 刷新/synchronize 同步
update 更新/revert 复原,
lock 锁定/unlock 解锁
check out 签出/check in 签入,
submit 提交/commit 交付
push 推/pull 拉,
expand 展开/collapse 折叠
begin 起始/end 结束,
start 开始/finish 完成
enter 进入/exit 退出,
abort 放弃/quit 离开
obsolete 废弃/depreciate 废旧,
collect 收集/aggregate 聚集
```

##### 3) 常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。

正例： `MAX_STOCK_COUNT`

反例： `MAX_COUNT`

## 关于分号

- 不要使用分号。 (参见：[1](http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding)，[2](http://inimino.org/%7Einimino/blog/javascript_semicolons)，[3](https://www.youtube.com/watch?v=gsfbh17Ax9I))

  eslint: [`semi`](http://eslint.org/docs/rules/semi)

  ```js
  window.alert('hi') // ✓ ok
  window.alert('hi'); // ✗ avoid
  ```

- 不要使用 `(`, `[`, or `` ` `` 等作为一行的开始。在没有分号的情况下代码压缩后会导致报错，而坚持这一规范则可避免出错。

  eslint: [`no-unexpected-multiline`](http://eslint.org/docs/rules/no-unexpected-multiline)

  ```js
  // ✓ ok
  ;(function() {
    window.alert('ok')
  })()(
    // ✗ avoid
    (function() {
      window.alert('ok')
    })()
  )
  ```

  ```js
  // ✓ ok
  ;[1, 2, 3]
    .forEach(bar)

    [
      // ✗ avoid
      (1, 2, 3)
    ].forEach(bar)
  ```

  ```js
  // ✓ ok
  ;`hello`.indexOf('o')// ✗ avoid
  `hello`.indexOf('o')
  ```

  备注：上面的写法只能说聪明过头了。

  相比更加可读易懂的代码，那些看似投巧的写法是不可取的。

  譬如：

  ```js
  ;[1, 2, 3].forEach(bar)
  ```

  建议的写法是：

  ```js
  var nums = [1, 2, 3]
  nums.forEach(bar)
  ```

## 拓展阅读

- [An Open Letter to JavaScript Leaders Regarding Semicolons][1]
- [JavaScript Semicolon Insertion – Everything you need to know][2]

##### 一个值得观看的视频：

- [JavaScript 中的分号多余吗？- YouTube][3]

当前主流的代码压缩方案都是基于词法（AST-based）进行的，所以在处理无分号的代码时完全没有压力（何况 JavaScript 中分号本来就不是强制的）。

##### 一段摘抄自 _["An Open Letter to JavaScript Leaders Regarding Semicolons"][1]_ 这篇文章的内容：

> [自动化插入分号的做法]是安全可依赖的，而且其产出的代码能够在所有浏览器里很好地运行。 Closure compiler, yuicompressor, packer 还有 jsmin 都能正确地对这样的代码进行压缩处理。并没有任何性能相关的问题。
>
> 不得不说，Javascript 社区里的大牛们一直是错误的，并不能教给你最佳实践。真是让人忧伤啊。 我建议先弄清楚 JS 是怎样断句的（还有就是哪些地方看起来断了其实并没有），明白了这个后就可以随心写出漂亮的代码了。
>
> 一般来说， `\n` 表示语句结束，除非：
>
> 1. 该语句有未闭合的括号， 数组字面量， 对象字面量 或者其他不能正常结束一条语句的情况（譬如，以 `.` 或 `,` 结尾）
> 2. 该语句是 `--` 或者 `++` （它会将后面的内容进行自增或减）
> 3. 该语句是 `for()`，`while()`，`do`，`if()` 或者 `else` 并且没有 `{`
> 4. 下一行以 `[`，`(`，`+`，`*`，`/`，`-`，`,`，`.` 或者其他只会单独出现在两块内容间的二元操作符。
>
> 第一条很容易理解。即使在 JSLint 中，也允许 JSON，构造器的括号中，以及使用 `var` 配合 `,` 结尾来声明多个变量等这些情中包含 `\n`。
>
> 第二条有点奇葩。 我还想不出谁会（除了这里用作讨论外）写出 `i\n++\nj` 这样的代码来，不过，顺便说一下，这种写法最后解析的结果是 `i; ++j`，而不是 `i++; j`。
>
> 第三条也容易理解。 `if (x)\ny()` 等价于 `if (x) { y() }`。解释器会向下寻找到代码块或一条语句为止。
>
> `;` 是条合法的 JavaScript 语句。所以 `if(x);` 等价于 `if(x){}`，表示 “如果 x 为真，什么也不做。” 这种写法在循环里面可以看到，就是当条件判断与条件更新是同一个方法的时候。 不常见，但也不至于没听说过吧。
>
> 第四条就是常见的 “看，说过要加分号！” 的情形。但这些情况可以通过在语句前面加上分号来解决，如果你确定该语句跟前面的没关系的话。举个例子，假如你想这样：
>
> ```js
> foo()
> ;[1, 2, 3].forEach(bar)
> ```
>
> 那么完全可以这样来写：
>
> ```js
> foo();
> [1, 2, 3].forEach(bar)
> ```
>
> 后者的好处是分号比较瞩目，一旦习惯后便再也不会看到以 `(` 和 `[` 开头又不带分号的语句了。

[1]: http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding
[2]: http://inimino.org/~inimino/blog/javascript_semicolons
[3]: https://www.youtube.com/watch?v=gsfbh17Ax9I
