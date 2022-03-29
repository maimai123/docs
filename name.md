# 命名规范

> 计算机科学只存在两个难题：缓存失效和命名
> -- Phil Karlton

## 正确拼写单词

> 不要拼错单词，不要拼错单词，不要拼错单词

很简单，在 vscode 中安装 [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) 插件。错误的单词拼写下方会有绿色的线提示。并且可以用`command` + `.`进行快速更正

## 命名原则

- <span style="color: red;">语义化，见名知意，鼓励使用多个单词</span>
- 最后一个单词，能说明变量代表的含义的本质(比如 List 或者 s 结尾就知道是个列表，Detail 结尾知道是个对象，Params 结尾，知道是代表参数的对象)

## 缩写

### <span style="color: red;">永远不要为了少打字而使用缩写，除非这个缩写人尽皆知。</span>

> 非人尽皆知的缩写会带来沟通成本

```js
// bad
un = 'A Person Name' // .....
// 现在编译器能通过单词的一部分来自动提示。长的命名并不会带来任何的坏处
// 而且所有的变量都会在代码压缩后变成无意义的字母
// good
userName = 'A Person Name'
```
#### 项目命名

全部采用小写方式， 以中划线分隔。

正例：`mall-management-system`

反例：`mall_management-system / mallManagementSystem`

## 文件名

全部采用小写方式， 以中划线分隔，有复数结构时，要采用复数命名法， 缩写不用复数

正例： `scripts / styles / components / images / utils / layouts / demo-styles / demo-scripts / img / doc`

反例： `script / style / demo_scripts / demoStyles / imgs / docs`

#### React 组件

Pascal Case 大驼峰。

> 保证与文件的默认导出名一致。因为 React 的组件名必须大写。所以文件名用大驼峰。并且，使用 jsx 而不是 js 作为文件名。这样能让人一看就知道是组件。

#### Vue 组件

Pascal Case 大驼峰。

> Vue 的组件最后默认导出的是一个逻辑上的单例配置项，按照惯例，单例对象是需要大写的。因此使用大驼峰

#### 样式文件

kebab case，短横线命名法。

#### 定义常量、枚举和字典的文件

统一用`constant.js`

## 文件夹

#### 如果是一个页面或者一个组件

请保持命名与与入口文件默认导出的类名、方法名、函数名、常量名一致。

####  常用文件夹名

```
源码：src
配置：config
文档：docs
路由：routes
构建脚本：build
bash脚本：scripts
组件：components
样式：styles
图片：images
字体：fonts
公共库：libs
store：stores
mock数据：mock
```

#### 其它情况

使用短横线命名法。

#### 命名严谨性

代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。 说明：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式也要避免采用

正例：`henan / luoyang / rmb 等国际通用的名称，可视同英文。`

反例：`DaZhePromotion [打折] / getPingfenByName() [评分] / int 某变量 = 3`


#### HTML

推荐使用 HTML5 的文档类型申明： <!DOCTYPE html>.
（建议使用 text/html 格式的 HTML。避免使用 XHTML。XHTML 以及它的属性，比如 application/xhtml+xml 在浏览器中的应用支持与优化空间都十分有限）。

- 规定字符编码
- IE 兼容模式
- 规定字符编码
- doctype 大写

正例：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta http-equiv="X-UA-Compatible" content="IE=Edge" />
    <meta charset="UTF-8" />
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company" />
  </body>
</html>
```

## JavaScript

#### 避免用一个字母命名，让你的命名可描述。（来自 Airbnb 的代码规范）

> 除了 map, reduce, filter 等高阶函数。
> 命名长度在现代的 JS 引擎下对性能的影响几乎可以忽略不计

```js
// bad
function q() {
  // ...
}
// good
function query() {
  // ...
}
```

#### 用小驼峰式命名你的对象、函数、实例。（来自 Airbnb 的代码规范）

```js
// bad
const OBJEcttsssss = {}
const this_is_my_object = {}
function c() {}
// good
const thisIsMyObject = {}
function thisIsMyFunction() {}
```

#### 用大驼峰式命名类。（来自 Airbnb 的代码规范）

```javascript
// bad
function user(options) {
  this.name = options.name
}
const bad = new user({
  name: 'nope'
})
// good
class User {
  constructor(options) {
    this.name = options.name
  }
}
const good = new User({
  name: 'yup'
})
```

#### 不要用前置或后置下划线。（来自 Airbnb 的代码规范）

> Why? JavaScript 没有私有属性或私有方法的概念。尽管前置下划线通常的概念上意味着“private”，事实上，这些属性是完全公有的，因此这部分也是你的 API 的内容。这一概念可能会导致开发者误以为更改这个不会导致崩溃或者不需要测试。 如果你想要什么东西变成“private”，那就不要让它在这里出现。
> 总结一句就是这么做没有任何效果，那为什么要做呢。在火眼中甚至能看到公共方法都这么命名的。

```javascript
// bad
this.__firstName__ = 'Panda'
this.firstName_ = 'Panda'
this._firstName = 'Panda'
// good
this.firstName = 'Panda'
```

### 不要保存引用`this`， 用箭头函数或[函数绑定——Function#bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)（Airbnb）

> 保存 this 在 es5 时代的代码中很常见，但现在有了 ES6，请使用更短更易读的实现。

```javascript
// bad
function foo() {
  const self = this
  return function() {
    console.log(self)
  }
}
// bad
function foo() {
  const that = this
  return function() {
    console.log(that)
  }
}
// good
function foo() {
  return () => {
    console.log(this)
  }
}
```

#### export default 导出模块 A，则这个文件名也叫 A.\*， import 时候的参数也叫 A。 大小写完全一致。（这也是上面的文件命名的原因（Airbnb））

```javascript
// file 1 contents
class CheckBox {
// ...
}
export default CheckBox;
// file 2 contents
export default function fortyTwo() { return 42; }
// file 3 contents
export default function insideDirectory() {}
// in some other file
// bad
import CheckBox from './checkBox'; // PascalCase import/export, camelCase filename
import FortyTwo from './FortyTwo'; // PascalCase import/filename, camelCase export
import InsideDirectory from './InsideDirectory'; // PascalCase import/filename, camelCase export
// bad
import CheckBox from './check_box'; // PascalCase import/export, snake_case filename
import forty_two from './forty_two'; // snake_case import/filename, camelCase export
import inside_directory from './inside_directory'; // snake_case import, camelCase export
import index from './inside_directory/index'; // requiring the index file explicitly
import insideDirectory from './insideDirectory/index'; // requiring the index file explicitly
// good
import CheckBox from './CheckBox'; // PascalCase export/import/filename
import fortyTwo from './fortyTwo'; // camelCase export/import/filename
import insideDirectory from './insideDirectory'; // camelCase export/import/directory name/implicit "index"
// ^ supports both insideDirectory.js and insideDirectory/index.js
```

#### 当你 export-default 一个函数时，函数名用小驼峰，文件名需要和函数名一致（Airbnb）。

```javascript
function makeStyleGuide() {
  // ...
}
export default makeStyleGuide
```

#### 当你 export 一个结构体/类/单例/函数库/对象 时用大驼峰（Airbnb）。

**特别地，vue 文件视为一个单例或类**

```javascript
const AirbnbStyleGuide = {
  es6: {}
}
export default AirbnbStyleGuide
```

#### 简称和缩写应该全部大写（Airbnb）。

> Why? 名字都是给人读的，不是为了适应电脑的算法的。

```javascript
// bad
import SmsContainer from './containers/SmsContainer'
// bad
const HttpRequests = [
  // ...
]
// good
import SMSContainer from './containers/SMSContainer'
// good
const HTTPRequests = [
  // ...
]
```

#### 你可以用全大写字母设置静态变量，他需要满足三个条件（Airbnb）。

    1. 导出变量
    2. 是 `const` 定义的， 保证不能被改变
    3. 这个变量是可信的，他的子属性都是不能被改变的
    > Why? 这是一个附加工具，帮助开发者去辨识一个变量是不是不可变的。
    - 对于所有的 `const` 变量呢？ —— 这个是不必要的。大写变量不应该在同一个文件里定义并使用， 它只能用来作为导出变量。 赞同！
    - 那导出的对象呢？ —— 大写变量处在export的最高级(e.g. `EXPORTED_OBJECT.key`) 并且他包含的所有子属性都是不可变的。

```javascript
// bad
const PRIVATE_VARIABLE = 'should not be unnecessarily uppercased within a file';
// bad
export const THING_TO_BE_CHANGED = 'should obviously not be uppercased';
// bad
export let REASSIGNABLE_VARIABLE = 'do not use let with uppercase variables';
// ---
// allowed but does not supply semantic value
export const apiKey = 'SOMEKEY';
// better in most cases
export const API_KEY = 'SOMEKEY';
// ---
// bad - unnecessarily uppercases key while adding no semantic value
export const MAPPING = {
KEY: 'value'
};
// good
export const MAPPING = {
key: 'value'
};
```

#### 如果属性/方法是`boolean`， 用 `isVal()` 或 `hasVal()（Airbnb）`

> 这样做更符合方法所做的事情

```javascript
// bad
if (!dragon.age()) {
  return false
}
// good
if (!dragon.hasAge()) {
  return false
}
```

#### 数组以`s`或者`List`结尾

英语中的`s`代表某名词的复数形式。
另外`xxxxList`比起`xxxxArray`更符合语义。

```jsx
// Very Bad Arr这个缩写在火眼代码中出现了无数次
const userArr = []
// good
const users = []
const userList = []
```

## CSS

#### CSS 类名

- 类名使用小写字母，以中划线分隔
- id 采用驼峰式命名
- scss 中的变量、函数、混合、placeholder 采用驼峰式命名

ID 和 class 的名称总是使用可以反应元素目的和用途的名称，或其他通用的名称，代替表象和晦涩难懂的名称

不推荐：
```css
.fw-800 {
  font-weight: 800;
}

.red {
  color: red;
}
```
推荐:
```
.heavy {
  font-weight: 800;
}

.important {
  color: red;
}
```

#### 尽量使用缩写属性

不推荐：

```css
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;
```

推荐：

```css
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
```

#### cssModules


1)css 选择器中避免使用标签名
从结构、表现、行为分离的原则来看，应该尽量避免 css 中出现 HTML 标签，并且在 css 选择器中出现标签名会存在潜在的问题。

2)很多前端开发人员写选择器链的时候不使用 直接子选择器（注：直接子选择器和后代选择器的区别）。有时，这可能会导致疼痛的设计问题并且有时候可能会很耗性能。然而，在任何情况下，这是一个非常不好的做法。如果你不写很通用的，需要匹配到 DOM 末端的选择器， 你应该总是考虑直接子选择器。


```jsx
import styles from './style.less'
const foo = () => {
  // good
  return <div className={styles['are-you-ok']} />
  // bad
  return <div className={styles.areYouOk} />
}
```

不推荐:

```css
.content .title {
  font-size: 2rem;
}
```

推荐:

```css
.content > .title {
  font-size: 2rem;
}
```

#### 每个选择器及属性独占一行
不推荐：
```
button{
  width:100px;height:50px;color:#fff;background:#00a0e9;
}
```
推荐：
```
button{
  width:100px;
  height:50px;
  color:#fff;
  background:#00a0e9;
}
```
#### 省略0后面的单位
不推荐：
```
div{
  padding-bottom: 0px;
  margin: 0em;
}
```
推荐：
```
div{
  padding-bottom: 0;
  margin: 0;
}
```

#### 避免使用ID选择器及全局标签选择器防止污染全局样式
不推荐：
```css
#header{
  padding-bottom: 0px;
  margin: 0em;
}
```
推荐：
```
.header{
  padding-bottom: 0px;
  margin: 0em;
}
```

### LESS 规范

#### 代码组织
##### 1)将公共less文件放置在style/less/common文件夹
例:// color.less,common.less


##### 2)按以下顺序组织
1、@import;
2、变量声明;
3、样式声明;
```
@import "mixins/size.less";

@default-text-color: #333;

.page {
  width: 960px;
  margin: 0 auto;
}
```
#### 1.4.2 避免嵌套层级过多
 将嵌套深度限制在3级。对于超过4级的嵌套，给予重新评估。这可以避免出现过于详实的CSS选择器。
避免大量的嵌套规则。当可读性受到影响时，将之打断。推荐避免出现多于20行的嵌套规则出现

不推荐：
```less
.main{
  .title{
    .name{
       color:#fff
    }
  }
}
```
推荐：
```
.main-title{
   .name{
      color:#fff
   }
}
```


#### Vue style 块中的类名

kebab 命名法。同 css 全局属性

## 常量命名

全大写，单词间用下划线隔开

```jsx
export const PRIMARY_COLOR = '#b6782b'
```

## 枚举命名

见[枚举与常量](./enum.md)

## 事件回调

以`on`开头

```jsx
onSummaryExport = () => {}
```

```jsx
<input onChange={onNameChange} />
```

## 发起 Ajax 请求方法名

#### 获取列表

`fetch` + 请求资源名 + `List`

```js
@action fetchUserList() {
}
```

#### 获取资源详情

`fetch` + 资源名 + `Detail`

```js
@action fetchUserDetail() {
}
```

#### 获取数据可视化中图的数据（此场景在火眼中出现较多）

`fetch` + 资源名 + `Chart`

```js
@action fetchMediaRealTimeChart() {
}
```

#### 创建资源

`create` + 资源名

```js
@action createUser() {
}
```

#### 修改资源

`update` + 资源名

```js
@action updateUser() {
}
```

#### 删除资源

`remove` + 资源名

```js
@action removeUser() {
}
```
