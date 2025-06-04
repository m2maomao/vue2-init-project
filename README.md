# 手动初始化Vue 2 + Vite项目
# node -v v20.8.0
## 步骤 1：初始化Vite项目（选择Vanilla模板）
```
npm create vite@latest my-vue2-project -- --template vanilla
cd my-vue2-project
npm install vue@2.7.14 @vitejs/plugin-vue2 vue-template-compiler --save
npm install vite@5 --save-dev
```
## 步骤 2：修改项目结构
### 2.1 删除无用文件：
```
rm src/main.js src/style.css
```
### 2.2 创建Vue 2所需文件：
```
mkdir src/components
touch src/App.vue src/main.js
```
## 步骤 3：配置关键文件
### 3.1 vite.config.js（启用Vue 2支持）
```
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue2'

export default defineConfig({
  plugins: [vue()],
  // 如果需要JSX支持
  esbuild: {
    jsxFactory: 'h',
    jsxFragment: 'Fragment'
  }
})
```
### 3.2 src/main.js（Vue 2入口文件）
```
import Vue from 'vue'
import App from './App.vue'

new Vue({
  render: h => h(App)
}).$mount('#app')
```
### 3.3 src/App.vue（根组件）
```
<template>
  <div id="app">
    <h1>Vue 2 + Vite</h1>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello World!'
    }
  }
}
</script>

<style scoped>
h1 {
  color: #42b983;
}
</style>
```
### 3.4 index.html（修改挂载点）
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Vue 2 + Vite</title>
</head>
<body>
  <div id="app"></div>
  <script type="module" src="/src/main.js"></script>
</body>
</html>
```
## 步骤 4：添加基础功能（可选）
### 添加Vue Router
```
npm install vue-router@3
```
### 创建 src/router/index.js：
```
import Vue from 'vue'
import Router from 'vue-router'
import Home from '../views/Home.vue'

Vue.use(Router)

export default new Router({
  routes: [
    { path: '/', component: Home }
  ]
})
```
### 添加Vuex
```
npm install vuex@3
```
### 创建 src/store/index.js：
```
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.Store({
  state: { count: 0 },
  mutations: {
    increment(state) {
      state.count++
    }
  }
})
```
## 步骤 5：运行项目
```
npm run dev
```



