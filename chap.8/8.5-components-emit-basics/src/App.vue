<script setup lang="ts">
import { ref } from 'vue'
import OneSection from './components/OneSection.vue'

const randInit = Math.floor(Math.random() * 10)
const rand = ref(randInit)
const onCreateNewRand = () => {
  rand.value = Math.floor(Math.random() * 10)
}
</script>

<template>
  <section class="box">
    <p>親コンポーネントで乱数を表示: {{ rand }}</p>
    <OneSection v-bind:rand="rand" v-on:createNewRand="onCreateNewRand" />
  </section>
</template>

<style scoped>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>
