<template>
  <div id="app">
    <Header></Header>
    <router-view/>
  </div>
</template>

<style>
  @import './assets/styles/header.css';
  @import './assets/styles/main.css';
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
