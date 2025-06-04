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