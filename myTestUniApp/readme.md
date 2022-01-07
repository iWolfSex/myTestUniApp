
##目录结构
```
pages 页面存放目录
static 静态文件资源目录
App.vue 引用入口文件 和小程序app.js类似
main.js 应用入口文件 注册Vue等
manifest.json 项目配置
pages.sson 页面配置
uni.scss 全局配置

common 存放公用的文件
component 存放自定义组件
store vuex目录
unpackage 编译后的文件存放目录
```

##笔记
```
 v-bind:可以简写成: 组件属性要使用data中定义的数据变量，或者组件属性要是使用表达式
 v-on:可以简写成@ 绑带事件
 v-model 数据双向绑定
 v-if条件判断,决定某个内容或区域是否挂载
 v-show：条件判断，是否显示 
 v-for:列表渲染
 ```
 ##事件绑定
  v-on:可以简写成@ 
  使用.stop 可以阻止事件的穿透
  ```
  <view @click="c1">
  	我是父级
  	<view @click.stop="c2">我自子级</view>
  </view>
  
  ```
  ##自定义组件
  
```
 使用easycom规范（components 目录下创建目录，组件名通组件目录名），可以直接使用组件
  父组件向子组件传递数据用 props
  子组件向父组件传递数据可以通过 自定义事件 父组件自定义事件 子组件触发父组件定义的事件，并传递数据
  子组件可以定义插槽 让父组件自定义要显示的内容
 ```
 ## 布局相关的
```
 px em rem vh wh rpx
 推荐使用rpx,会根据不同的设备进行换算
 750宽度下 2rpx = 1px
 推荐使用flex
```


