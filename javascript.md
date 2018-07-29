## Web 前端 JavaScript 命名规范指引

# 全局规范
**强制** 不得出现无意义的命名，

**强制** 代码中的命名均不能以下划线或美元符号开始，也不能以下划线或美元符号结束。

反例：_name / __name / $Object / name_ / name$ / Object$

**强制** 代码中的命名严禁使用拼音与英文混合的方式，不允许直接使用中文的方式。

反例：zhangshan / wodemingzi / mydiannao / 我的电脑

**强制** 不得出现无意义的命名。

反例：aaa / aaccc / eefff / abc123

**强制** 方法名、参数名、变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式。

正例： localValue / getHttpMessage() / inputUserId


# 代码格式
**强制** 采用 2 个空格缩进，禁止使用 tab 字符。如果使用 tab 缩进，必须设置 1 个 tab 为 2 个空格。

**强制** 句末必须用分号结尾。

**强制** 大括号的使用约定。如果是大括号内为空，则简洁地写成 {} 即可，不需要换行；如果是非空代码块则大括号内容换行输入。

正例：
``` javascript
if (true) {
  // something
} else{
  // something
}
```
反例：
``` javascript
if (true)
{
  // something
}
else
{
  // something
}
```
**强制** 关键词、条件括弧后面使用空格；运算操作符号两侧使用空格；语句分割符「,」后面使用空格。

反例：if (空格 a == b 空格)

**强制** if/for/while/switch/do 等保留字与括号之间都必须加空格。

示例：
``` javascript
if (true) {
  // something
}
```
**强制** 任何二目、三目运算符的左右两边都需要加一个空格。

正例：
``` javascript
for (let i = 0; i < 6; i++) {
  if (i === 5) {
    // something
  }
}
```
反例：
``` javascript
for (let i=0; i<6; i++) {
  if (i===5) {
    // something
  }
}
```

**强制** 注释的双斜线与注释内容之间有且仅有一个空格。

正例：// 注释内容，注意在//和注释内容之间有一个空格。

**强制** IDE 的 text file encoding 设置为 UTF-8; IDE 中文件的换行符使用 Unix 格式，不要使用 Windows 格式。

**强制** 方法参数在定义和传入时，多个参数逗号后边必须加空格。

正例：
``` javascript
function Hi(first, middle, last) {}
```

# 控制语句
**强制** 在一个 switch 块内，每个 case 要么通过 break/return 等来终止，要么注释说明程序将继续执行到哪一个 case 为止；在一个 switch 块内，都必须包含一个 default 语句并且放在最后，即使它什么代码也没有。

**强制** 在 if/else/for/while/do 语句中必须使用大括号「{}」，即使只有一行代码。

**强制** 控制语句的嵌套不得超过 5 层，大于 5 层的请另写方法。

**建议** 在进行比较时，建议用全等「===」来代替「==」。

**建议** 除常用方法（如 getXxx/isXxx）等外，不要在条件判断中执行其它复杂的语句，将复杂逻辑判断的结果赋值给一个有意义的布尔变量名，以提高可读性。

正例：
``` javascript
var isSome = 1 !== '1' || 2 !== '2';
if (isSome) {
  // something
}
```

# 注释规范
**强制** 类、函数方法的注释必须使用 JsDoc 规范， arguments 、 return 等必须做出解释。

说明：在 IDE 编辑窗口中，JsDoc 方式会提示相关注释，生成 JsDoc 可以正确输出相应注释，不进入方法即可悬浮提示方法、参数、返回值的意义，提高阅读效率。

更多 JsDoc 块标签参考文档后面 [注释1](#注释1)；

正例：
``` javascript
/**
 * 方法名
 *
 * @param {Number} num
 * @param {String} isSomeString
 * @param {Boolean} isSome
 * @returns {Boolean} returnSome
 */
```
反例：
``` javascript
// 方法名
```
**强制** 所有类、全局函数必须写上创建者的名称、及创建时间，如有修改者，也必须在创建者下方续写修改者名称、及修改时间。

示例：
``` javascript
/**
 * 方法名
 * ...
 * ...
 * ...
 * @creator darlang
 * @creatTime 20xx.xx.xx
 * @editor darlang
 * @editTime 20xx.xx.xx
 */
```
**强制** 方法内部单行注释，在被注释语句上方另起一行，使用//注释。方法内部多行注释使用/* */注释，注意与代码对齐。

**建议** 好的命名、代码结构是自解释的，注释力求精简准确、表达到位。避免出现过多随意的注释，代码的逻辑一旦修改，修改注释是相当大的负担。


# 文件命名
**强制** 文件名统一使用小写英文表意，单词间用下划线分割「_」。

**建议** 项目结构应该包含 images 图像文件夹、css 样式文件夹、js 脚本文件夹、fonts 字体文件夹

```
|---- index.html
|---- js/
|---- js/libs/
|---- css/
|---- fonts/
|---- images/
```

# 其他
**强制** JS调试使用 `console.log()` 及 `console.dir()` 进行，避免使用弹出框，线上版需要注释所有调试代码

**建议** 表单输入及其他业务流程，必须校验输入内容。

**建议** 避免使用 eval()，setTimeOut使用调用函数，考虑重绘，回流操作对页面影响。

**建议** eslint 代码校验建议遵循[注释2](#注释2)

##### 注释1
| 块标签名称 | 作用注释 |
| ------ | ------ |
| @abstract/@virtual | 这个成员必须在继承类中实现（或重写）。 |
| @access | 指定该成员的访问级别（私有 private，公共 public，或保护 protected） |
| @alias | 标记成员有一个别名 |
| @augments/@extends | 指名这个子类继承至哪个父类，后面需要加父类名 |
| @author | 指定项目的作者 |
| @borrows | 这个对象使用另一个对象的某些东西 |
| @callback | 描述一个回调函数。 |
| @class/@constructor | 此函数旨在需要使用”new”关键字调用，即构造函数。 |
| @classdesc | 使用后面的文字来描述整个类 |
| @constant/@const | 记录一个对象作为一个常量 |
| @constructs | 这个函数成员将成为类的构造函数 |
| @copyright | 描述一些版权信息 |
| @default/@defaultvalue | 记录默认值 |
| @deprecated | 说明这已不再是首选方法,即已经弃用 |
| @description/@desc | 描述一个标识 |
| @enum | 描述一个相关属性的集合。 |
| @event | 描述一个事件。 |
| @example | 提供一个如何使用描述项的例子。 |
| @exports | 标识一个由JavaScript模块导出的成员。 |
| @external | 标识一个外部的类，命名空间，或模块。 |
| @file/@fileoverview/@ | 描述一个文件 |
| @fires/@emits | 描述事件这个方法可能会触发。 |
| @function/@fun/@method | 描述一个函数或方法。 |
| @global | 记录一个全局对象。 |
| @ignore | 忽略文档中的一个标识。 |
| @implements | 这个标识实现一个接口。 |
| @inheritdoc | 指明这个标识应继承其父类的文档 |
| @inner | 描述一个内部对象。 |
| @instance | 记录一个实例成员。 |
| @interface | 这是别人可以实现的一个接口。 |
| @kind | 标识的类型。 |
| @lends | 将一个字面量对象的所有属性标记为某个标识符（类或模块）的成员。 |
| @license | 标识你的代码采用何种软件许可协议。 |
| @listens | 列出一个标识的监听事件。 |
| @member/@var | 记录一个成员。 |
| @memberof | 标明这个标识属于哪个父级标识。 |
| @mixes | 此对象混入了另一个对象中的所有成员。 |
| @mixin | 记录一个mixin（混入）对象。 |
| @module | 记录一个 JavaScript 模块。 |
| @name | 记录一个对象的名称。 |
| @namespace | 记录一个命名空间对象。 |
| @override | 指明一个标识符覆盖其父类同名的标识符。 |
| @param/@arg/@argument | 记录传递给一个函数的参数 |
| @private | 标记为私有的。 |
| @property/@prop | 记录一个对象的属性。 |
| @protected | 标记为受保护的。 |
| @public | 标记为公开的。 |
| @readonly | 标记为只读的。 |
| @requires | 这个文件需要一个 JavaScript 模块。 |
| @returns/@return | 记录一个函数的返回值。 |
| @see | 更多详细信息请参阅其他一些文档。 |
| @since | 此功能何时被添加进来的? |
| @static | 记录一个静态成员。 |
| @summary | 完整描述的一个简写版本。 |
| @this | this关键字的指向 |
| @throws | 说明可能会被抛出什么样的错误。 |
| @todo | 记录一个将要完成的任务。 |
| @tutorial | 插入一个链接到包含教程文件。 |
| @type | 记录一个对象的类型。 |
| @typedef | 记录一个自定义的类型。 |
| @variation | 区分具有相同名称的不同的对象。 |
| @version | 记录版本信息 |

##### 注释2
``` javascript
module.exports = {
  "env": {
    "browser": true,
    "es6": true,
    "jquery": true,
    "node": true
  },
  "globals": {
  },
  "extends": "eslint:recommended",
  "parserOptions": {
    "ecmaVersion": 6,
    "sourceType": "module",
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "rules": {
    "indent": ["error", 2],
    "strict": "off",
    "no-unused-vars": "warn",
    "no-console": "warn",
    "comma-dangle": ["off", "always"],
    "eqeqeq": "warn",
    "linebreak-style": ["error", "unix"],
    "quotes": ["off", "double"],
    "semi": ["error", "always"]
  }
};
```