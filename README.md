# Applets_cloud-music
模拟网易云音乐小程序  [相关资料](https://github.com/junjieweb/Applets_cloud-music/tree/data)
# 小程序

## 1. 数据绑定

1. Vue

   1. 数据流

      1. 单向数据流

   2. 实现了双向数据绑定

      1. v-model
      2. input事件

   3. 修改状态数据

      1. this.key = value

      2. 同步修改

         

2. React

   1. 单向数据流
   2. 修改状态数据
      1. this.setState()
         1. 自身的钩子函数（componentDIdMount）: 异步
         2. 非自身的钩子函数（setTimeout): 同步

3. 小程序

   1. 单向数据流
   2. 修改状态数据
      1. 同步修改
      2. this.setData()



## 2. 事件流

### 2.1 标准事件流

1. 捕获阶段

  2. 执行目标阶段
  3. 冒泡阶段

### 2.2 非标准事件流

1. 目标： IE

  2. 特点: 没有捕获阶段

### 2.3 小程序

​	bind + 事件名: 冒泡事件

​	catch + 事件名: 非冒泡事件

## 3. 获取用户基本信息

### 3.1 

 	1. 首次登陆，未授权的情况
 	  	1. <button open-type='getUserInfo' />
 	  	2. 弹出授权窗口进而获取用户信息

### 3.2

1. 授权以后再次登陆

  2. 注意： 授权的动作只发生一次
  3. wx.getUserInfo()

## 4. 前后端交互

1. 语法: 
   1. wx.request()
2. 注意点： 
   1. 小程序发请求之前需要在小程序后台管理的主界面设置请求的域名列表
   2. 小程序为了安全起见要求发送所有的请求必须是https协议
   3. 最大并发限制是 **10** 个；

## 5. 事件委托

1. 什么是事件委托
   1. 将子元素的事件委托(绑定)给父元素
2. 事件委托的好处
   1. 减少绑定次数，提高效率
   2. 节省内存空间
3. 事件委托的原理
   1. 冒泡
4. 触发事件的对象是谁
   1. 子元素
5. 如何找到触发事件的对象
   1. event.target
6. event.target VS event.currentTarget
   1. event.target绑定事件的对象不一定是触发事件的对象，比如： 事件委托
   2. event.currentTarget绑定事件的对象一定是触发事件的对象

## 6. 数据存储

1. 小程序Storage
   1. 单个key存储的上限是1M
   2. 所有数据的上限是10M
   3. 等同于H5的localStorage，相当于永久存储
   4. 方法： setStorage || setStorageSync
2. 面试题
   1. localStorage
      1. 永久存储， 硬盘中存储
      2. 存储量5M
   2. sessionStorage
      1. 会话存储，存储在内存中
      2. 存储量5M
   3. cookie
      1. 服务器端生成， 保存在浏览器端
      2. 存储量4KB
      3. 分类
         1. 持久化cookie
         2. 会话cookie
      4. 问题
         1. 浏览器端每次和服务器端交互的时候都会携带cookie，会浪费带宽
         2. cookie容易被截获并且伪造，不安全、
         3. 被token取代
   4. session
      1. 服务器端生成，保留在服务器端
      2. 通常使用cookie作为载体存放session字段



## 7. 路由传参

1. 小程序
   1. 方式： query
   2. 示例: url?key=vlaue
   3. 获取： 目标页面onLoad声明周期函数中通过实参获取
2. Vue
   1. 方式: 
      1. params: 需要占位符
      2. query: 查询字符串
      3. meta: 路由元信息
      4. props
         1. 布尔值
         2. 对象
         3. 函数
3. React
   1. 方式: 
      1. query: 不方便获取
      2. params: 经常使用



## 8. 自定义事件

1. 绑定事件
   1. 事件名
   2. 事件的回调函数
   3. 声明事件对象参数(标准事件中的event)
   4. 获取数据的一方
   5. 对比: 
      1. PubSub: 订阅
      2. Vue: $on()
2. 触发事件
   1. 事件名
   2. 传入事件对象(自定义的，等同于event)
   3. 提供数据的一方
   4. 对比： 
      1. PubSub: 发布
      2. Vue: $emit()
