Web To Native Rules (vision: 20190611)
===========================
该文件作为前端跟native端共同讨论后的版本

****

## 目录
* [js 判断Android和iOS](#differentiate)
* [token 获取方式](#token)
* [web 访问 native 说明](#webToNative)
* [native 调用 js 函数说明](#nativeToWeb)
* [web 访问 native 并获取返回值](#webToNativeAndCallback)
* [其它说明](#others)

differentiate
------
js 判断Android和iOS的代码如下：
```
var isAndroid = window.navigator.appVersion.match(/android/gi);
var isIPhone = window.navigator.appVersion.match(/iphone/gi);
```

token
------
由于Android与iOS交互方式不同，为了方便统一，token我们建议统一用localstorage存储管理。
而且由于需要获取token的地方很多，建议统一让Android和iOS端直接存入localstorage。js直接在任何地方从localstorage获取。

```
localStorage.setItem('token', 'token');
localStorage.getItem('token');
```

webToNative
------
- web调用native的方法需要区分Android跟iOS
- 传值一律用JSON string的形式传输，务必注意JSON格式，最好是直接调用JSON.stringify()对对象进行格式化，这样格式不容易出错。
- 相互调用的函数名需要统一用一个sheet去管理

### 示例如下：
- 调用iOS方式：
```
window.webkit.messageHandlers.自定义函数名.postMessage(JSON.stringify(params));
```
- 调用Android方式：
```
window.messageHandlers.自定义函数名(JSON.stringify(params));
```

nativeToWeb
------
因为native可以直接访问到webview的全局环境变量，所以native可以直接访问js的全局函数，我们直接将函数需要native调用的函数写在全局环境下就可以了。

webToNativeAndCallback
------
调用native方法并需要返回值，Android和iOS有很大不同
- 调用iOS获取返回值方式：
首先告诉native开始调用
```
window.webkit.messageHandlers.自定义函数名.postMessage(JSON.stringify({callback: callbackFnName}));
```
然后native再去调用js全局函数
```
function callbackFnName(returnVal) {
	console.lot('native返回值': returnVal);
}
```
- 调用Android并获取返回值：
调用Android就直接可以获取到返回值
```
var returnVal = window.messageHandlers.自定义函数名();
console.lot('native返回值': returnVal);
```

others
------
- 所有的函数名以及传输参数格式和内容都要用sheet统一管理
- 所有参数的传输必须用JSON格式化的形式传输
- 判断Android和iOS必须用一个方法统一调用
