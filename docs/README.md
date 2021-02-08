# 前端开发规范 @MYKG.AI

## 前言

规范的目的是为了**编写高质量的代码**，让团队成员每天**心情愉悦**，大家在一起是快乐的。

?> _引自《阿里规约》的开头片段：_<br/><br/>
现代软件架构的复杂性需要协同开发完成，如何高效地协同呢？无规矩不成方圆，无规范难以协同，比如，制订交通法规表面上是要限制行车权，实际上是保障公众的人身安全，试想如果没有限速，没有红绿灯，谁还敢上路行驶。对软件来说，适当的规范和标准绝不是消灭代码内容的创造性、优雅性，而是限制过度个性化，以一种普遍认可的统一方式一起做事，提升协作效率，降低沟通成本。代码的字里行间流淌的是软件系统的血液，质量的提升是尽可能少踩坑，杜绝踩重复的坑，切实提升系统稳定性，码出质量。

心有猛虎，细嗅蔷薇。虽然身为晨兴夜寐的打工人，猫牙的开发者们也在不断追求着设计开发的三大境界：**健全(robust)** 、**弹性(elastic)** 、**优雅(elegant)** 。为了极大化把控软件质量以及提高内部人员的综合素质，在经历了多个项目的协作打磨完善后，猫牙技术团队基于「传递信息的有效性，文字大于口述」的理念撰写了此文。

猫牙一项坚持✊ **约定大于配置(convention over configuration)** 的编码风格，以及 **声明式大于命令式(declarative over imperative)** 的设计风格。本文依据约束力的强弱，将规约的等级分为<i class='must'></i>、<i class='should'></i>、<i class='better'></i>三类，其中强制需要落实到项目中去，并应当作为code review的参考依据。

本文中将涉及到多种命名方式。参考[《Medium - Case Styles》](https://medium.com/better-programming/string-case-styles-camel-pascal-snake-and-kebab-case-981407998841)这篇文章中的命名，本文将使用`小驼峰`或`驼峰`指代camelCase，`大驼峰`指代PascalCase，`蛇形`指代snake_case，`大蛇形`指代SNAKE_CASE_ALL_CAP，`肉串`指代kebab-case。

## 一、基础规范

### 1.1 命名规范

> <i class='must'></i>**严谨性命名**：所有编程相关的命名不要使用拼音和英文混合的方式，更不允许直接使用中文汉字的方式。

<em class='notice'>说明：正确的英文拼写和语法可以让阅读者易于理解，避免歧义。</em>

<em class='notice'>注意：纯拼音命名方式尽量避免采用；正常的英文单词不要拆分开；ali / youku / hangzhou 等国际通用名称，可视同为英文。</em>

正例：rmb / seafood

反例：sea_food / getPingfenByName() / colors['红色']

> <i class='should'></i>**语义化命名**：所有编程器相关的命名，均需体现其含义。

<em class='notice'>注意：特殊情况无法从命名体现含义时，需要添加额外注释给出解释；代表复数的变量，末尾使用 s / set / list / array 等标识。</em>

正例：comments / commentList / uidSet / getUsers()

反例：comment[1] / let uidSet = getUid() / data

> <i class='must'></i>**一致性命名**：一个项目中应该维护其术语表，同一个术语不应拥有两个命名。

正例：comment.vue / commentDate.vue

反例：comment.vue / replyDate.vue

> <i class='should'></i>**集成式命名**：同一类组件应通过尾缀区分开，或将归类至子文件夹中。

<em class='notice'>说明：方便查看目录时归类文件。</em>

正例：dialog-stundet.html / dialog-teacher.html / dialog/student.html / dialog/teacher.html

反例：student-dialog.html / teacher-dialog.html

> <i class='must'></i>**杜绝不规范缩写**，避免望文不知义。

反例：AbstractClass“缩写”命名成 AbsClass；condition“缩写”命名成 condi，此类随意缩写严重降
低了代码的可阅读性。

> <i class='must'></i>**项目命名**全部采用小写方式， 以中划线分隔。

正例：mall-management-system

反例：mall_management-system / mallManagementSystem

> <i class='must'></i>**文件夹命名**全部采用小写方式， 以中划线分隔。

正例： img

反例： Img

> <i class='must'></i>**js文件命名**项目中全部采用肉串或全部采用小驼峰的方式。

正例： date-util.js

反例： DateUtil.js

> <i class='should'></i>**css、scss、html、svg文件命名**项目中全部采用肉串方式。

正例： date-picker.html

反例： datePicekr.html

### 1.2 HTML规范

> <i class='must'></i>**缩进**：使用2个空格(一个tab)。

<em class='notice'>说明：部分编辑器需要需改tab的Spaces，修改为两个空格符。</em>

> <i class='better'></i>**语义化标签**，HTML5 中新增很多语义化标签，所以优先使用语义化标签，避免一个页面都是div或者p标签。

<em class='notice'>说明：一方面加强seo的效果，另一方面加强代码可读性。</em>

正例：

```html
<header></header>
<footer></footer>
```

反例：

```html
<div>
  <p></p>
</div>
```

> <i class='better'></i>**引号**：优先使用双引号。

正例：

```html
<input name="input" />
```

反例：

```html
<input name='input' />
```

> <i class='should'></i>不要出现style。

### 1.3 CSS规范

> **命名**
> - <i class='must'></i>类名使用肉串。
> - <i class='should'></i>id采用小驼峰。
> - <i class='should'></i>scss中变量采用肉串，函数采用小驼峰。

> **选择器**
> - <i class='better'></i>尽量避免css中出现HTML标签。
> - <i class='better'></i>总是考虑使用`子代选择器`还是`后代选择器`。

反例：

```css
.content .title {
  font-size: 2rem;
}
```

正例：

```css
.content > .title {
  font-size: 2rem;
}
```

> <i class='better'></i>尽量使用缩写属性。

反例：

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

正例：

```css
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
```

> <i class='must'></i>每个选择器及属性独占一行。

反例：

```css
button{
  width:100px;height:50px;color:#fff;background:#00a0e9;
}
```

正例：

```css
button{
  width:100px;
  height:50px;
  color:#fff;
  background:#00a0e9;
}
```

> <i class='must'></i>省略0后面的单位。

反例：

```css
div{
  padding-bottom: 0px;
  margin: 0em;
}
```

正例：

```css
div{
  padding-bottom: 0;
  margin: 0;
}
```

> <i class='better'></i>减少使用ID选择器及全局标签选择器防止污染全局样式。

反例：

```css
#header{
  padding-bottom: 0px;
  margin: 0em;
}
```

正例：

```css
.header{
  padding-bottom: 0;
  margin: 0;
}
```

### 1.4 SCSS规范

> <i class='must'></i>**代码组织**：引入及变量搁置文件开头。

正例：

```scss
@import "mixins/size.scss";

$default-text-color: #333;

.page {
  width: 960px;
  margin: 0 auto;
}
```

> <i class='better'></i>减少嵌套层级过多。

<em class='notice'>说明：将嵌套深度限制在3级。对于超过4级的嵌套，给予重新评估。这可以避免出现过于详实的CSS选择器；避免大量的嵌套规则。当可读性受到影响时，将之打断。推荐避免出现多于20行的嵌套规则出现。</em>

反例：

```scss
.main{
  .title{
    .name{
       color:#fff
    }
  }
}
```

正例：

```scss
.main .title{
   .name{
      color:#fff
   }
}
```

### 1.5 Javascript规范

> <i class='must'></i>类名使用大驼峰。

正例：class Dockia {}

反例：class dockia {}

> <i class='must'></i>变量名使用小驼峰。

<em class='notice'>注意：代码中的命名均不能以下划线，也不能以下划线或美元符号结束。</em>

<em class='notice'>注意：布尔值使用`is`开头或其他可以体现出其布尔值默认值的单词。</em>

正例：isOpen / isLoading

反例：loading

> <i class='must'></i>常量命名使用大蛇形。

<em class='notice'>注意：方法中尽量不要出现魔法值(即未经预先定义的常量)。</em>

> <i class='must'></i>方法名使用小驼峰。\
> <i class='better'></i>方法名中动词的顺序应优先于名词，命名即体现出方法的作用。

正例：saveShopCarData() /openShopCarInfoDialog()

反例：save() / open() / show() / go()

> <i class='must'></i>行尾不要添加`;`。

正例：

```js
let studentList = []
```

反例：

```js
let studentList = [];
```

> <i class='must'></i>使用2个空格进行缩进。\
> <i class='better'></i>不同逻辑、不同语义、不同业务的代码之间插入一个空行分隔开来以提升可读性。

<em class='notice'>注意：任何情形，没有必要插入多个空行进行隔开。</em>

正例：

```js
if (x < y) {
  x += 10
} else {
  x += 1
}
```

> <i class='should'></i>尽可能省略代码行数。\
> <i class='should'></i>多使用链式的写法，换行需要缩进。

正例：

```js
let chosenStudentList = propStudentList.filter(i => i.isSelected)

let chosenStudentIdList = propStudentList
  .filter(i => i.isSelected)
  .map(i => i.id)
```

反例：

```js
let chosenStudentList = propStudentList.filter(i => {
  return i.isSelected
})

let chosenStudentIdList = propStudentList
.filter(i => i.isSelected)
.map(i => i.id)
```

> <i class='must'></i>字符串优先使用单引号或`。

正例:

```js
let str = 'foo'
let testDiv = `${str}`
```

反例:

```js
let str = "foo"
let testDiv = "<div id='test'></div>"
```

> <i class='better'></i>大括号中如果是单行内容，可以省略大括号。\
> <i class='must'></i>只有大括号中只包含return时，可以省略换行符。

正例：

```js
if (condition) return

if (condition) 
  doSomething()
```

反例：

```js
if (condition) {
  doSomething()
}

if (condition) doSomething()
```

> <i class='must'></i>永远不要直接使用 undefined 进行变量判断；使用 typeof 和字符串’undefined’对变量进行判断。

正例：

```js
if (typeof person === 'undefined') {
  // do something...
}
```

反例：

```js
if (person === undefined) {
  // do something...
}
```

> <i class='must'></i>条件运算符只可以替换一组if...else...。如果超出，改为使用if...else...或function。

正例：

```js
let text = isStudent ? '学生' : '老师'
```

反例：

```js
let text = isStudent ? '学生' : isMale ? '男老师' : '女老师'
```

> <i class='should'></i>配置 > 逻辑，优先维护易拓展的数据模型，而不是编写额外代码。

正例：

```js
let sizeEnum = {
  'small': 0,
  'big': 1
}

const getSizeNum = (size) => {
  return sizeEnum[size]
}
```

反例：

```js
const getSizeNum = (size) => {
  if (size == 'small') 
    return 0
  else if (size == 'big')
    return 1
  return null
}
```

> <i class='must'></i>**方法内注释**：双斜线后，必须跟一个空格；缩进与下一行代码保持一致；可位于一个代码行的末尾，与代码间隔一个空格

正例：

```js
if (condition) {
    // if you made it here, then all security checks passed
    allowed();
}

var zhangsan = 'zhangsan'; // one space after code
```

> <i class='must'></i>**方法注释**需要使用多行注释。各类标签@param, @method等请参考[usejsdoc](http://usejsdoc.org/)和[JSDoc Guide](http://yuri4ever.github.io/jsdoc/)

正例：

```js
/**
 * @func
 * @desc 一个带参数的函数
 * @param {string} a - 参数a
 * @param {number} b=1 - 参数b默认值为1
 * @param {string} c=1 - 参数c有两种支持的取值</br>1—表示x</br>2—表示xx
 * @param {object} d - 参数d为一个对象
 * @param {string} d.e - 参数d的e属性
 * @param {string} d.f - 参数d的f属性
 * @param {object[]} g - 参数g为一个对象数组
 * @param {string} g.h - 参数g数组中一项的h属性
 * @param {string} g.i - 参数g数组中一项的i属性
 * @param {string} [j] - 参数j是一个可选参数
 */
function foo(a, b, c, d, g, j) {
  // do something...
}
```

> <i class='must'></i>**临时注释代码**：临时注释代码，需要注明操作人以及为什么关闭或者什么时候打开的注释。

正例：

```js
// 0207 goddy 等2.0版本开启
// let studentList = []
```

> <i class='must'></i>**未完成/bug标记注释**：需要使用`// TODO: ...`或者`// FIXME: ...`标识。

正例：

```js
// FIXME: 接入正式的接口替换掉mock数据

// TODO: 优化查询速度
```

> <i class='better'></i>慎用console.log。\
> <i class='should'></i>打印日志，应在前面标注出打印的内容是什么。否则，应该从代码中删除。

<em class='notice'>因console.log大量使用会有性能问题，所以在非webpack项目中谨慎使用log功能。</em>

正例：

```js
console.log('==== debug: student list ===')
console.log(studentList)
```

## 二、Vue规范

### 2.1 构建规范

> <i class='should'></i>使用最新版的**vue-cli脚手架**来初始化项目，项目名按照上面的命名规范。
> - <i class='should'></i>选用`Babel`向下兼容低版本浏览器(babel配置文件另存新文件)。
> - <i class='should'></i>开启`Progressive Web App (PWA) Support`。
> - <i class='must'></i>开启`Router`。根据项目情况决定使用history / hash模式。
> - <i class='must'></i>使用`scss`。
> - <i class='better'></i>使用`jest`进行单元测试。

### 2.3 其他

> <i class='better'></i>所有命名尽量与后端命名统一。

## 三、附录

### 3.1 函数方法常用的动词

[](_appendix/verb.md ':include')
