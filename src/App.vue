<template>
  <div id="app">
    <Header></Header>
    <section id="main">
      <router-view/>
    </section>
  </div>
</template>

<script>
import Header from '@/components/header/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>
