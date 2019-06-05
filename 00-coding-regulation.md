regulation (vision: 20190605)
===========================
该文件作为Monstar-lab前端小组统一规范

****

## 目录
* [Css](#css规则)
* [JavaScript](#JavaScript规则)
* [HTML](#HTML规则)
* [JSX](#JSX规则)
* [页面完成的标准](#页面完成条件)

css规则
------
- css 每个选择器之间严格空一行，规则内部不能空行
- 每一条规则的第一个{前面加空格，结尾}单独一行
```
.header {
    width: 5px;
}
```
- 所有命名用小写字母+数字+中划线组成
- css不能超过四层
- 字体和图标字体使用偶数大小
```
.wrap {
    font-size: 14px;
}
```
- 为0的值省略单位
```
.wrap {
    font-size: 0;
}
```
- 不要使用 !important
- 将媒体查询放在尽可能相关规则附近
- 将动画代码尽可能放在相关规则附近
- 属性选择器或属性值用双引号
- 每个声明必须用分号结束
- 保证每行语句都是多行
- 当前选择器的@extentd和@include放在每个规则前面
- 保持规范的缩进


JavaScript规则
------
- 变量不能用保留字
- 常量大写
- js 中字符串使用单引号
- 严格代码缩进
- 函数之间严格空一行
- 比较少用的语法和业务逻辑一定加上注释，在注释前加上空行
- 函数参数不超过两个，如果超过就传入对象，使用es6的结构语法
- 如果通过 if 和 else 使用多行代码块，把 else 放在 if 代码块关闭括号的同一行
- 使用空格把运算符隔开
- 在使用长方法链时进行缩进。使用前面的点 . 强调这是方法调用而不是新语句
- js语句不加分号（加分号）
- 使用驼峰式命名对象、函数和实例
- 使用帕斯卡式命名构造函数或类
- 代码块中避免多余留白
```javascript
if (user) {
    const name = getName()
}
```
### 注释首尾留一个
```javascript
// comment
```


HTML规则
------
- 文件首行以```<!DOCTYPE …>```定格开始
- 文件以小写字母开头和命名，以减号连接
- 必须声明charset
- 将script放在文件底部，样式表放在head中
- 保持规范的缩进
- 使用小写元素名，小写属性名，自定义属性写在data-*中
- 每个元素都添加关闭标签
- img标签必须要alt属性
- HTML属性使用双引号


JSX规则
------
- 多个属性，多行书写，每个属性占用一行，标签结束另起一行
```javascript
<Foo
    superLongParam='bar'
    annotherSuperLongParam='baz'
/>
// 如果组件的属性可以放在一行就保持在当前一行中
<Foo bar='bar' />
```
- 始终在自闭合标签前面添加一个空格
```javascript
<Foo />
```
- 属性书写始终以驼峰命名法
- 用括号包裹多行 JSX 标签
```javascript
render () {
    return (
        <MyComponent className='long body' foo='bar'>
          <MyChild />
        </MyComponent>
    )
}
```
- 当标签没有子元素时，始终使用自闭合标签
- 尽量避免在 componentDidMount 中调用 this.setState
- 不要在 componentWillUpdate/componentDidUpdate/render 中调用 this.setState
- 值为 true 的属性可以省略书写值
```javascript
<Hello personal />
```


页面完成条件
------
- 自测没有bug，或者按照测试用例测试通过
- 需要在不同浏览器上面测试通过
- 手机端不能有 hover 效果
- PC端 button、链接需要有 hover 效果
- 代码严格遵循了规范
