<script setup lang="ts">
import { ref } from 'vue'
import OneInfo from './components/OneInfo.vue'

const PropsTitle = ref('発生した乱数')
const rand = Math.round(Math.random() * 100)
const propsContent = ref(rand)
</script>

<template>
  <h1>Props基礎</h1>
  <section>
    <h2>テンプレート変数を利用</h2>
    <OneInfo v-bind:title="PropsTitle" v-bind:content="propsContent" />
  </section>
</template>

<style scoped>
.box {
  border: blue 1px solid;
  margin: 10px;
}
</style>
