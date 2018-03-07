<template>
  <div id="translateOutput">
    <h2>{{translatedText}}</h2>
  </div>
</template>

<script>
  export default {
    name: 'translateOutput',
    props:['translatedText'],//使用props属性接收父组件传递的数据
  }
</script>

<style>
</style>
