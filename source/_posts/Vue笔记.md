---
title: Vue从入门到放弃
---

## 一、Vue.js入门
https://cn.vuejs.org/v2/guide/installation.html

### 例子
#### 1.1、Hello World
[点击查看运行结果](https://lixin360589712.github.io/vue_demo/helloWorld.html)

<details>
<summary>点击查看源码</summary>
```html
<!DOCTYPE html>
<html>
  <head>
    <title>My first Vue app</title>
    <!-- 文件头中引入vue.js包,根据场景不通引入下方其中一个 -->
    <!-- 开发环境版本，包含了有帮助的命令行警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <!-- 生产环境版本，优化了尺寸和速度 -->
    <!-- <script src="https://cdn.jsdelivr.net/npm/vue"></script> -->
  </head>
  <body>
    <div id="app">
      {{ message }}
    </div>
    <script>
      var app = new Vue({
        el: "#app",
        data: {
          message: "Hello World!"
        }
      });
    </script>
  </body>
</html>
```
</details>

##### 知识点：引入Vue.js包 、声明式渲染
	1）声明式渲染
	Vue.js 的核心是一个允许采用简洁的模板语法来声明式地将数据渲染进 DOM 的系统。
	2）理解响应式操作
	Vue为响应式的，打开浏览器控制台（console），直接修改app.message值，例子也会相应的更新。注意我们不再和 HTML 直接交互了。
	一个 Vue 应用会将其挂载到一个 DOM 元素上 (对于这个例子是 `#app`) 然后对其进行完全控制。那个 HTML 是我们的入口，但其余都会发生在新创建的 Vue 实例内部。
#### 1.2、鼠标悬停案例
<details>
<summary>点击查看源码</summary>
```
<!DOCTYPE html>
<html>
  <head>
      <title>Vue demo hello world!</title>
      <!-- 开发环境版本，包含了有帮助的命令行警告 -->
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      <!-- 生产环境版本，优化了尺寸和速度 -->
      <!-- <script src="https://cdn.jsdelivr.net/npm/vue"></script> -->
  </head>
  <body>
    <div id="app2">
        <span v-bind:title="message">
            鼠标悬停几秒查看此处动态绑定的提示信息
        </span>
    </div>
    <script>
    var app2 = new Vue({
      el: "#app2",
      data: {
        message: '页面加载于' + new Date().toLocaleString()
      }
    });
    </script>
  </body>
</html>
```
</details>

<details>
<summary>点击查看运行结果</summary>
<!DOCTYPE html>
<html>
  <head>
      <title>Vue demo hello world!</title>
      <!-- 开发环境版本，包含了有帮助的命令行警告 -->
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      <!-- 生产环境版本，优化了尺寸和速度 -->
      <!-- <script src="https://cdn.jsdelivr.net/npm/vue"></script> -->
  </head>
  <body>
    <div id="app2">
        <span v-bind:title="message">
            鼠标悬停几秒查看此处动态绑定的提示信息
        </span>
    </div>
    <script>
    var app2 = new Vue({
      el: "#app2",
      data: {
        message: '页面加载于' + new Date().toLocaleString()
      }
    });
    </script>
  </body>
</html>
</details>

##### 指令：v-bind
##### 知识点：绑定元素指令
	绑定元素指令 attribute：
	例子中的attribute v-bind 被称为指令，指令带有前缀 v- 以表示它们是 Vue 提供的特殊 attribute，它们会在渲染的 DOM 上应用特殊的响应式行为。
	v-bind:title="message" 指令的意思是：“将这个元素节点的 title attribute 和 Vue 实例的 message property 保持一致”。

#### 1.3、条件 v-if
<details>
<summary>点击查看源码</summary>
```
<!DOCTYPE html>
<html>
  <head>
      <title>Vue demo hello world!</title>
      <!-- 开发环境版本，包含了有帮助的命令行警告 -->
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      <!-- 生产环境版本，优化了尺寸和速度 -->
      <!-- <script src="https://cdn.jsdelivr.net/npm/vue"></script> -->
  </head>
  <body>
    <div id="app3">
        <p v-if="seen">现在你看到我了</p>
    </div>
    <script>
    var app3 = new Vue({
      el: "#app3",
      data: {
        seen: true
      }
    });
    </script>
  </body>
</html>
```
</details>

<details>
<summary>点击查看运行结果</summary>
<!DOCTYPE html>
<html>
  <head>
      <title>Vue demo hello world!</title>
      <!-- 开发环境版本，包含了有帮助的命令行警告 -->
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      <!-- 生产环境版本，优化了尺寸和速度 -->
      <!-- <script src="https://cdn.jsdelivr.net/npm/vue"></script> -->
  </head>
  <body>
    <div id="app3">
        <p v-if="seen">现在你看到我了</p>
    </div>
    <script>
    var app3 = new Vue({
      el: "#app3",
      data: {
        seen: true
      }
    });
    </script>
  </body>
</html>
</details>

可以在控制台输入app3.seen = false 或者app3._data.seen = false,会发现之前显示的消息消失了。

##### 指令 v-if（条件）
##### 知识点：把数据绑定到 DOM 文本或 attribute
	这个例子演示了我们不仅可以把数据绑定到 DOM 文本或 attribute，还可以绑定到 DOM 结构。此外，Vue 也提供一个强大的过渡效果系统，可以在 Vue 插入/更新/移除元素时自动应用过渡效果。

#### 1.3、循环 v-for
<details>
<summary>点击查看源码</summary>
```html
<!DOCTYPE html>
<html>
  <head>
    <title>My first Vue app</title>
    <!-- 文件头中引入vue.js包,根据场景不通引入下方其中一个 -->
    <!-- 开发环境版本，包含了有帮助的命令行警告 -->
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <!-- 生产环境版本，优化了尺寸和速度 -->
    <!-- <script src="https://cdn.jsdelivr.net/npm/vue"></script> -->
  </head>
  <body>
    <div id="app-4">
      <ol>
        <li v-for="todo in todos">
          {{ todo.text }}
        </li>
      </ol>
    </div>
    <script>
      var app4 = new Vue({
        el: '#app-4',
        data: {
          todos: [
            { text: '学习 JavaScript' },
            { text: '学习 Vue' },
            { text: '整个牛项目' }
          ]
        }
      })
    </script>
  </body>
</html>
```
</details>

<details>
<summary>点击查看运行结果</summary>
<!DOCTYPE html>
<html>
  <head>
      <title>Vue demo hello world!</title>
      <!-- 开发环境版本，包含了有帮助的命令行警告 -->
      <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
      <!-- 生产环境版本，优化了尺寸和速度 -->
      <!-- <script src="https://cdn.jsdelivr.net/npm/vue"></script> -->
  </head>
  <body>
    <div id="app4">
      <ol>
        <li v-for="todo in todos">
          {{ todo.text }}
        </li>
      </ol>
    </div>
    <script>
      var app4 = new Vue({
        el: '#app4',
        data: {
          todos: [
            { text: '学习 JavaScript' },
            { text: '学习 Vue' },
            { text: '整个牛项目' }
          ]
        }
      })
    </script>
  </body>
</html>
</details>



## 二、Vue-router

## 三、Vuex

