# MonstarLab Chengdu Front-end Test Pyramid 

## ■Definition
前端测试金字塔提供了一个前端测试内容的架构规范。
The front-end test pyramid is a representation of how a front end test suite should be structured.

它有三方面的测试内容构成：基本覆盖的单元测试、页面的快照测试和少量的端对端测试。The ideal test suite is comprised of unit tests, some snapshot tests, and a few end to end (e2e) tests.


## ■Purpose
运用快速失败的原则，降低开发阶段的方法逻辑、显示错误，提高前端单体测试交付质量，提高回归测试速度。


## ■Unit tests

### Tool

Jest.js -- unit test case

### 内容

#### A.方法返回的值正确
Functions return the correct result.

e.g. 

     日期格式化：Format time 
     
     全角字符转半角字符：Format DBC to SBC
      
#### B.方法调用后，组件行为改变符合预期

Trigger actions on the components and check that the components behave as expected.


e.g. 

     点赞的方法调用后，点赞的样式改变
     
     手机菜单按钮点击后，菜单出现

### Pass standard

测试代码或手动测试；

定义的全部方法返回值正确；

方法调用后，组件的样式改变符合预期。



## ■Snapshot tests

### 内容

#### 页面元素是否正确渲染

对比设计图


#### 测试多浏览器

> 工具 Tool

BrowserStack https://www.browserstack.com/

> 常规规范 Normal rule

Chrome / Safari / FF / IE11 / Android 5 / IOS 9

#### 响应式页面测试

> Tool

浏览器的开发者工具 /
BrowserStack https://www.browserstack.com/

> Normal rule
 
````1200/768/320````级别终端

#### 像素对比

****Tool:**** 

PerfectPixel (Chrome plugin)    

PhantomCSS https://github.com/HuddleEng/PhantomCSS (npm package)


### 合格标准 Pass standard

页面内容符合设计图或者画面定义书(Must);

响应式适配美观(should);

要求适配的浏览器没有样式错乱(Must);

UI设计图1px高度还原或者与画面定义书式样一致（should）。


## ■End to end tests (e2e)

### 工具 Tool

Jest.js -- unit test case


交互事件是否响应正确


ajax是否正常

错误处理是否正确

### 合格标准 Pass standard

画面定义书定义的功能正确实现；

稳定功能块的e2e测试代码覆盖(50%)或手动测试通过；

正常流程的e2e测试代码覆盖(50%)或手动测试通过；

异常处理的手动测试通过。


## References

https://medium.freecodecamp.org/the-front-end-test-pyramid-rethink-your-testing-3b343c2bca51
https://www.oschina.net/translate/the-front-end-test-pyramid-rethink-your-testing