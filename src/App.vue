<script setup lang="ts">
import HeaderComponent from './components/HeaderComponent.vue'
</script>

<template>
  <HeaderComponent />
  <RouterView />
</template>

<style lang="sass">
@import './assets/sass/variable.sass'
@import './assets/sass/main.sass'
body, h1, h2, h3, h4, h5, h6, p
  margin: 0
</style>
