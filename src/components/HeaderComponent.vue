<script lang="ts" setup>
import { useRouter } from 'vue-router'

const router = useRouter()
</script>
<template>
  <el-menu
    class="header space-around"
    mode="horizontal"
    :ellipsis="false"
    text-color="#555555"
    active-text-color="#8EC63F"
  >
    <el-menu-item index="0" @click="router.push({ name: 'home' })">CIC</el-menu-item>
    <div class="flex-grow"></div>
    <el-menu-item index="1"  @click="router.push({ name: 'aboutus' })">About us</el-menu-item>
    <el-menu-item index="2"  @click="router.push({ name: 'signup' })"> Sign up </el-menu-item>
    <el-menu-item index="3"  @click="router.push({ name: 'login' })"> Log in </el-menu-item>
  </el-menu>
</template>

<style lang="sass" scoped>
@import '@/assets/sass/variable'
.header
  display: flex
  align-items: center
  position: sticky
  top: 0
  z-index: 100
  height: 60px
.flex-grow
  flex-grow: 1
</style>
