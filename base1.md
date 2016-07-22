## ```js```的数据类型

* 基本类型: ```Undefined```、```Null```、```Boolean```、```Number```、```String```
* 引用类型: ```Object```、```Array```、```Date```、```RegExp```、```Function```

## ```js```的与运算和或运算的注意点

### 逻辑与
* 如果有一个操作数为```null( NaN、undefined )```，则返回```null( NaN、undefined )```。
* 如果第一个操作数是对象则返回第二个操作数。
* 如果第二个操作数是对象，只有在第一个操作数的求值结果为```true```时才会返回该对象。

逻辑与属于短路操作，第一个操作数结果为```false```时，就不会对第二个操作数求值，直接短路返回```false```。

### 逻辑或
* 如果两个操作数都为```null( NaN、undefined )```，则返回```null( NaN、undefined )```。
* 如果第一个操作数是对象则返回第一个操作数。
* 如果第一个操作数求值结果为```false```，则返回第二个操作数。

逻辑或也属于短路操作，第一个操作数结果为```true```时，就不会对第二个操作数求值，直接短路返回```true```。

## ```js```闭包的理解

当某个函数调用时会创建一个执行环境以及作用域链，然后根据```arguments```和其它命名参数初始化形成活动对象。在外部函数调用结束后，
其执行环境与作用域链被销毁，但是其活动对象保存在了闭包之中，最后在闭包函数调用结束后才销毁。简单的说，闭包就是能够读取其他函数内部变量的函数。
在```js```中，闭包是指有权访问另一个函数作用域中的变量的函数。

### 闭包的作用
* 匿名自执行函数

有的场景下函数只需要执行一次，例如```init()```之类的函数，其内部变量无需维护，我们可以使用闭包。 我们创建了一个匿名的函数，
并立即执行它，由于外部无法引用它内部的变量，因此在函数执行完后会立刻释放资源，而且**不污染全局对象**。

* 封装

模拟面向对象的代码风格进行封装，使私有属性存在成为可能。

### 缺点
* 常驻内存，会增大内存使用量，易造成内存泄露


## ```js```跨域的解决方案

### ```JSONP```
原理:网页通过添加一个```<script>```元素，向服务器请求```JSON```数据，这种做法不受同源政策限制；服务器收到请求后，将数据放在一个指定名字的回调函数里传回来。

#### 优点
* 兼容性好，简单易用，支持浏览器与服务器双向通信

#### 缺点
* 只支持GET请求
* 存在脚本注入以及跨站请求伪造等安全问题

### ```CORS```
跨域资源共享```(CORS)```允许浏览器向跨源服务器发送```AJAX```请求。需由服务器向浏览器发送一个响应标头```Access-Control-Allow-Origin```。如果浏览器检测到相应的设置，就可以允许```Ajax```进行跨域的访问。

### 通过修改```document.domain```来跨子域
在两个域名都属于同一基础域名且协议端口都一致的情况下，将子域和主域的```document.domain```设为同一个主域。

### 使用```window.name```来进行跨域
浏览器窗口有```window.name```属性。这个属性的最大特点是，无论是否同源，只要在同一个窗口里，所有的页面都是共享一个```window.name```的，每个页面对```window.name```都有读写的权限，```window.name```是持久存在一个窗口载入过的所有页面中的。

#### 优点

* ```window.name```容量很大，可以放置非常长的字符串。

#### 缺点

*  必须监听子窗口```window.name```属性的变化，影响网页性能。

### ```window.postMessage```

未完待续......