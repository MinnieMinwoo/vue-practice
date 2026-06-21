<script setup lang="ts">
import { computed, ref } from 'vue'

const number = ref(80)
const showOrNot = computed(() => {
  let showOrNot = false

  const rand = Math.floor(Math.random() * 100)
  if (rand > number.value) {
    showOrNot = true
  }

  return showOrNot
})
</script>

<template>
  <section>
    v-ifを利用
    <p v-if="showOrNot">条件に合致したので表示</p>
  </section>
  v-showを利用
  <p v-show="showOrNot">条件に合致したので表示</p>
</template>
