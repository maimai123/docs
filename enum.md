# 枚举与常量

## 魔术数字

程序设计中所谓的魔术数字（magic number）是指硬编码在代码里的具体数值（如“10”“123”等以数字直接写出的值）。虽然程序作者写的时候自己能了解数值的意义，但对其他程序员而言，甚至制作者本人经过一段时间后，会难以了解这个数值的用途，只能苦笑讽刺“这个数值的意义虽然不懂，不过至少程序能够运行，真是个魔术般的数字”而得名（起源参考平方根倒数速算法）。
**基于以下理由，代码中的任何地方不应该存在魔术数字**

- 数值的意义难以了解
- 数值需要变动时，可能要改不只一个地方

## 举个 🌰

```js
const price_tax = 1.05 * price
```

输入的价格（price）计算含税（price_tax）售价的程序。 但税率并不是万年不变，当政府调整税率时，会有修改程序的必要。 这里“1.05”就是一种魔术数字，“为什么是 1.05”会让人无法马上了解。 下面是去掉魔术数字的示例，程序容易了解也容易修正。

```js
const TAX = 0.05
const price_tax = (1.0 + TAX) * price
```

## 枚举

### 什么是枚举

**在数学和计算机科学理论中，一个集的枚举是列出某些有穷序列集的所有成员的程序，或者是一种特定类型对象的计数。这两种类型经常（但不总是）重叠。**
这么讲可能略抽象，举个例子，一个星期的七天，便是一个枚举。
**在代码中，任何值出现的范围在有限集内，并且与业务相关，则必须使用枚举的写法**

```js
/*
 * 一周七天的枚举
 * @enum {number}
 **/
const WeekType = {
  /* 星期一 **/
  MON: 1,
  /* 星期二 **/
  TUE: 2,
  /* 星期三 **/
  WED: 3,
  /* 星期四 **/
  THU: 4,
  /* 星期五 **/
  FRI: 5,
  /* 星期六 **/
  SAT: 6,
  /* 星期天 **/
  SUN: 7
}
```

## 如何用枚举和常量替换魔术数字

### 常量

```js
// 业务中经常会遇到设置某个状态为初始状态的代码，下面是没有代码复用的代码
class SomeComponent extends React.Component {
  state = {
    userConfig: {
      threshold: 0,
      type: SomeType.TYPE1,
      field: FieldType.FIELD2
    },
    modalVisible: false
  }
  resetUserConfig = () => {
    // userConfig和初始的state中的重复了
    this.setState({
      userConfig: {
        threshold: 0,
        type: SomeType.TYPE1,
        field: FieldType.FIELD2
      }
    })
  }
}
// 这么写就clear不少
const DEFAULT_USER_CONFIG = {
  threshold: 0,
  type: SomeType.TYPE1,
  field: FieldType.FIELD2
}
class SomeComponent extends React.Component {
  state = {
    userConfig: DEFAULT_USER_CONFIG,
    modalVisible: false
  }
  resetUserConfig = () => {
    this.setState({
      userConfig: DEFAULT_USER_CONFIG
    })
  }
}
```

### 枚举

1. 枚举统一写在`constant.js`文件中，全局使用到的枚举写在`lib/constant`下，其它情况下，写在业务代码目录下的`constant.js`中（没有就新建一个 QWQ）
1. 枚举对象用 Pascal Case（大驼峰）写法命名，强烈建议变量名以 Type 结尾
1. 枚举对象使用 jsdoc 注释，写明枚举中值的类型和枚举的使用场景
1. 枚举对象的 key 请全部大写，单词之间用分隔线隔开。
1. 建议在枚举对象的 key 上写上注释，说明枚举的这个字段是干什么的。比如下面的`DINGTALK`，可能其它同学不知道是钉钉的官方英文名

```js
/*
 * 警报功能的报警方式
 * @enum{number}
 **/
const AlertType = {
  /* 钉钉 **/
  DINGTALK: 1,
  /* 邮件 **/
  MAIL: 2
}
// ...
// ...
if (selectedAlertType === AlertType.DINGTALK) {
  // 处理报警方式为钉钉时的逻辑
}
```

经常我们需要从某个枚举字段得到他的中文字符串，便于在页面上显示，或者其它某个属性到另一属性的映射。
这种情况，应该这样写。

1. 字典名的变量也写在`constant.js`中
1. 字典的变量名全大写，以`MAP`结尾
1. 字典的 key 使用定义过的枚举，不允许直接使用数字
1. 使用字典时，用方括号`[]`获得字典中的值

```js
export const ALERT_TEXT_MAP = {
  [AlertType.DINGTALK]: '钉钉',
  [AlertType.MAIL]: '邮件'
}
// 做一些其它事情
const currentText = ALERT_TEXT_MAP[currentAlertType]
```

我们可以用上面的常量来生成选项数组。这个实现会在不久封装成公共方法供大家使用
下面代码中的 toPairs 是 lodash 中的一个方法，可以把`{ foo: 'bar', biz: 'bah' }`变成 `[['foo', 'bar'], ['biz', 'bah']]`，详情可以见[这里](https://kapeli.com/dash_share?docset_file=Lo-Dash&docset_name=Lodash&path=lodash.com/docs/4.17.html%23toPairs&platform=lodash&repo=Main&source=lodash.com/docs/4.17.10&version=4.17.11)
应该这样写

1. options 写在`constant.js`中
2. options 的变量名全大写，以`OPTIONS`结尾

```js
export const ALERT_TYPE_OPTIONS = toPairs(ALERT_TEXT_MAP).map(
  ([label, key]) => ({ label, key })
)
// 然后我们把ALERT_TYPE_OPTIONS传给组件就Van♂事了
return <CheckBoxGroup options={ALERT_TYPE_OPTIONS} />
```
