# 单体测试完成的条件
<a name="table-of-contents"></a>
## 目录

  1. [式样准确 must](#style)
  1. [效果完整 must](#effect)
  1. [定义的方法工作正常 must](#function)
  1. [遵守普遍规范 must](#common)

<a name="style"></a>
## 式样准确

#### ■高精度还原设计图 
+ 1px

#### ■页面各section比例符合设计期待
 
#### ■响应式适配符合设计期待或合理

#### ■background-image/image正确使用 更换图片后和设计效果表现一致

#### ■font符合设计，同等级font表现一致
+ family
+ size 
+ weight
+ color
+ align

#### ■color使用符合设计，同类对象color统一
+ font color
+ background color
+ wrapper-cover color

#### ■border样式符合设计或统一，同类对象border式样统一


#### ■form类式样符合设计或统一
    管理画面统一的规范参考：https://ant.design/

+ button
  + height
  + radius
  + min-width
  + width：100%留padding
  
+ input/textarea/checkbox/radio
  + height
  + radius
  
+ select
  + open/close样式
  + 点击外部收起

+ 报错信息位置，样式符合设计或统一


#### ■Feedback类出现条件和式样统一
    各个类对应的表现参考：https://ant.design/
+ alert
+ modal
+ message
+ Progress
+ notification

**[⬆Top](#table-of-contents)**



<a name="effect"></a>
## 效果完整

#### ■hove式样和动画符合设计或统一
+ button 
+ a href
    
#### ■active式样和动画符合设计或统一
+ header menu item
+ breadcrumb 

#### ■form类式样符合设计或统一
  + focus/blur/error/disable式样完整且统一
  

#### ■animation符合设计或统一
    效果 速度
+ hover
+ active
+ scroll
+ menu


**[⬆Top](#table-of-contents)**



<a name="function"></a>
## 定义的方法工作正常

#### ■函数输入输出符合预期
+ params
+ init value
+ computed value

#### ■绑定事件正确
+ 绑定成功
+ 没有重复绑定
+ 及时解绑

#### ■ 方法调用正确
+ 调用时机
+ 调用次数

**[⬆Top](#table-of-contents)**



<a name="common"></a>
## 遵守普遍规范

#### ■语言设定正确
+ en-US / en
+ ja-JP / ja
+ zh-CN / zh

#### ■LOGO  加链接 加hover

#### ■icon给大padding，确保点击范围
  + 注意SP难点中的问题


**[⬆Top](#table-of-contents)**