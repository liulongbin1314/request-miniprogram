## 安装

```bash
npm install @escook/request-miniprogram
```

## 导入

```js
// 按需导入 $http 对象
import { $http } from '@escook/request-miniprogram'

// 将按需导入的 $http 挂载到 wx 顶级对象之上，方便全局调用
wx.$http = $http

// 在 uni-app 项目中，可以把 $http 挂载到 uni 顶级对象之上，方便全局调用
uni.$http = $http
```

## 使用

### 支持的请求方法

```js
// 发起 GET 请求，data 是可选的参数对象
$http.get(url, data?)

// 发起 POST 请求，data 是可选的参数对象
$http.post(url, data?)

// 发起 PUT 请求，data 是可选的参数对象
$http.put(url, data?)

// 发起 DELETE 请求，data 是可选的参数对象
$http.delete(url, data?)
```

### 配置请求根路径

```js
$http.baseUrl = 'https://www.example.com'
```

### 请求拦截器

```js
// 请求开始之前做一些事情
$http.beforeRequest = function (options) {
  // do somethimg...
}
```

例 1，展示 loading 效果：

```js
// 请求开始之前做一些事情
$http.beforeRequest = function (options) {
  wx.showLoading({
    title: '数据加载中...',
  })
}
```

例 2，自定义 header 请求头：

```js
// 请求开始之前做一些事情
$http.beforeRequest = function (options) {
  if (options.url.indexOf('/home/catitems') !== -1) {
    options.header = {
      'X-Test': 'AAA',
    }
  }
}
```

### 响应拦截器

```js
// 请求完成之后做一些事情
$http.afterRequest = function () {
  // do something...
}
```

例如，隐藏 loading 效果：

```js
// 请求完成之后做一些事情
$http.afterRequest = function () {
  wx.hideLoading()
}
```

## 开源协议

![MIT](https://img.shields.io/badge/License-MIT-blue)

**enjoy!**
