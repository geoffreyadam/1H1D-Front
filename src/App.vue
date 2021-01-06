<template>
  <div id="app">
    <Header></Header>
    <router-view/>
  </div>
</template>

<style lang="less" scoped>
  @import './assets/styles/header.less';
  @import './assets/styles/main.scss';
</style>

<script>
import Header from '@/components/header/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>
