---
title: Vue从入门到放弃
---

## 一、Vue.js入门
### 入门引导
url:https://cn.vuejs.org/v2/guide/installation.html
#### 1.1、Hello World


文件头中引入vue.js包,根据场景不通引入下方其中一个



```html
<!DOCTYPE html>
<html>
  <head>
    <title>My first Vue app</title>
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
          message: "Hello Vue1!"
        }
      });
    </script>
  </body>
</html>
```



## 二、Vue-router

## 三、Vuex


