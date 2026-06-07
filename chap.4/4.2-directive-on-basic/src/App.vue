<script setup lang="ts">
import { ref } from 'vue'

const randomValue = ref('まだです')
const onButtonClick = () => {
  const rand = Math.round(Math.random() * 10)
  randomValue.value = String(rand)
}
</script>

<template>
  <section>
    <button v-on:click="onButtonClick">クリック！</button>
    <p>クリックの結果: {{ randomValue }}</p>
  </section>
</template>

<style scoped></style>
