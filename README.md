# towxml-steam-typer
> ##### 代码刚写完没多久，还在持续地完善中，所以当前你下载的版本一定不是稳定版，记得定时更新下代码，由于markdown语法的灵活复杂性，某些情况下难免会出问题。

> ##### 出问题请联系 QQ:3423729430 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 微信：zxx-zbl-wwj

> ##### 非常需要你的出错案例markdown文本

> github地址：https://github.com/zhouzxx/towxml-stream-typer

#### 介绍
用来解决流式数据太长，[towxml](https://github.com/sbfkcel/towxml) 重复渲染相同文本，导致越来越发烫卡顿的问题。通过自定义文字组件进行***局部渲染连续文本***、***样式布局稳定的节点进行复用,不再进行重复转化和渲染***两大核心思想，保证无论markdown文本再长，开始和结束都一样的丝滑，全程没有发烫，目前再安卓手机上测试了10分钟的文本，前后速度一致，没有发烫

#### 使用方式
1. 将 wxcomponents 下载下来，放到微信小程序代码或者 uniapp 代码的指定文件夹，作为一个组件使用，这和之前在项目中引用 towxml 是一样的
2. 和 towxml 的使用区别

由于定制了 towxml 的代码，所以 towxml 组件的 prop 参数发生了改变

目前的属性有：

| 属性名      | 类型               | 作用                                                         | 默认值 |
|-------------|-------------------|--------------------------------------------------------------|-------|
| mdText      | {text：String}    | 对象里面的text属性就是你的总的markdown 文本字符串，将你的流式数据转化为字符串，将text属性设置为最新的全部文本|
| speed       | Number            | 每多少秒打印一个字符，值越小打印越快，单位是毫秒，默认 10 毫秒打印一个字符 |10|
| isFinish    | Boolean           | 流式接口是否完成，即当你的流式接口数据返回已经结束了，将该属性设置为 true |false|
| openTyper   | Boolean           | 是否开启打字机，默认开启，如果你已经有完整 markdown 文本，想一次性渲染，就设为false |true|

##### 注意：mdText类型就是一个<span style="color: rgb(192,0,0);">普通对象</span>，如果你是使用uniapp,不要把这个对象设置为响应式对象，如果你使用原生小程序，当你把对象中的text属性改变了，也不要setData，因为我通过对象的引用就可以获取到最新的text内容。响应式或者自动更新反而会大大影响性能

目前的事件有：

finish：当打字机打印完毕，会发送 finish 事件，你可以通过该事件关闭滚动到底部的定时器等

3. uniapp的简单使用示例
[uniapp使用示例](https://gitee.com/zhou-xuxiang/towxml-steam-typer-uniapp-example)
