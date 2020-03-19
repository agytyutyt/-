# 前言

**[官方文档](https://cn.vuejs.org/v2/guide/)**

#  起步

## 1. Vue-Cli 构建项目

*需先安装好 node 环境*

1. 安装 Vue

   ~~~shell
   cnpm install vue -g
   ~~~

2. 安装 Vue-Cli 脚手架

   ~~~shell
   cnpm install vue-cli -g
   ~~~

3. 创建项目

   ~~~shell
   vue init webpack project_name
   ~~~

## 2. 项目主要文件

* index.html：项目承载文件
* src/main.js：是项目的主js文件，生成根实例；全局的使用的各种变量、js、插件 都在这里引入 、定义
* src/router/index.js：可简写为 router/，项目路由文件
* src/App.vue：项目根组件
* src/components/：项目组件文件夹

## 3. 文件关系

1. 用户访问 index.html
2. main.js 与 index.html 特定元素绑定，引入需要用的组件
3. main.js 产生根 Vue 实例，实例中绑定元素，引入路由、js、变量、插件等。
4. router 管理每一个路径所导向的组件
5. 每一个路径请求均指向 App.vue 这个根组件。
6. App.vue 设置 <router-view></router-view> 用于指明路由所指组件渲染的地方。
   （即组件将渲染到 App.vue 的 <router-view></router-view> 标签）

## 4. 文件详解

* main.js：

  ~~~js
  //导入所需组件
  import Vue from 'vue'
  import App from './App'
  import router from './router'
  
  Vue.config.productionTip = false
  
  //新建Vue实例
  new Vue({
    el: '#app',	//挂载 #app 元素上
    router,	//将路由引入到 Vue 实例中，方可使用
    components: { App },	//将组件引入 Vue 实例中，方可使用
    template: '<App/>'	//选择vue实例要加载哪个模板
  })
  ~~~

* App.vue：

  ~~~vue
  <template>
    <div id="app">
      <img src="./assets/logo.png">
      <router-view/>	<!-- 当用户访问到路由特定的路径时候，该路径所路由的组件讲在此处渲染 -->
        <myCom></myCom>	<!-- myCom 组件，在s cript 中的声明 -->
    </div>
  </template>
  
  <script>
    import myCom from '@/components/myCom'	//导入需要的组件
  export default {
    name: 'myCom'	//组件名称
    components: { 
    	myCom 	//声明使用哪些组件
    }
  }
  </script>
  ~~~

* myCom.vue：

  ~~~vue
  <template>
    <h1>Hello World!</h1>
  </template>
  
  <script>
  export default {
  }
  </script>
  ~~~

* router.js：

  ~~~js
  import Vue from 'vue'
  import Router from 'vue-router'
  import HelloWorld from '@/components/HelloWorld'
  import myCom from '@/components/myCom'
  
  Vue.use(Router)
  
  export default new Router({
    routes: [
      {
        path: '/',
        name: 'HelloWorld',
        component: HelloWorld
      },
      {
      	path: '/my',
      	name: 'myCom',
      	component: myCom
      }
    ]
  })
  ~~~

  

# Vue.js 组件使用

## 1、组件注册

* 使用 **<template></template>** 标签标识这是一个组件

  ~~~ Vue
  <template>
  	<h1>Hello World!</h1>
  </template>
  ~~~

* 使用 **export default** 进行组件声明，以使在其他页面中可对该组件进行 **导入** 。

  ~~~ js
  <script>
  export default {
    name: 'myHelloWorld'
  }
  </script>
  ~~~

## 2、组件使用

~~~ javascript
import myHelloWorld from '@/components/myHelloWorld'
// @/components/myHelloWorld 为components文件夹下的myHelloWorld.vue 文件
~~~



## 3、常用组件

* Vue

  ~~~ javascript
  import Vue from 'vue'
  ~~~

* Router

  ~~~ javascript
  import router from './router'
  //默认等价于 from './router/index.js'
  //若需要修改则直接指定文件名
  ~~~

* axios

  ~~~ javascript
  import axios from 'axios'
  ~~~



# Router 路由使用

## 1. 路由声明

~~~js
export default new Router (	//
	{
		path: 'route path',
    	name: 'name',
    	component: router to component
	}
)
~~~

## 2. 路由使用

​	

# 注意点

### 1、***export const*** 和 ***export default*** 

* export const: 命名导出

* export default: 默认导出

  ***注意***： export default 只可以有一个

  ​			export const 可以有多个

  ​			export const 可用于 export default 中，嵌套使用。

### 2、