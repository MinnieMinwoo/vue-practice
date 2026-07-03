<script setup lang="ts">
import {
  computed,
  onBeforeMount,
  onBeforeUpdate,
  onMounted,
  onRenderTracked,
  onRenderTriggered,
  onUpdated,
  ref,
} from 'vue'
import type { DebuggerEvent } from 'vue'

const heightInit = Math.round(Math.random() * 10)
const widthInit = Math.round(Math.random() * 10)
const height = ref(heightInit)
const width = ref(widthInit)

const area = computed(() => height.value * width.value)
const change = () => {
  height.value = Math.round(Math.random() * 10)
  width.value = Math.round(Math.random() * 10)
}

onBeforeMount(() => {
  console.log(`beforeMount called: ${height.value} x ${width.value}`)
})

onMounted(() => {
  console.log(`mounted called: ${height.value} x ${width.value}`)
})

onBeforeUpdate(() => {
  console.log(`beforeUpdate called: ${height.value} x ${width.value}`)
})

onUpdated(() => {
  console.log(`updated called: ${height.value} x ${width.value}`)
})

onRenderTracked((event: DebuggerEvent) => {
  console.log(`renderTracked called: ${height.value} x ${width.value}`)
  console.log(event)
})

onRenderTriggered((event: DebuggerEvent) => {
  console.log(`renderTriggered called: ${height.value} x ${width.value}`)
  console.log(event)
})
</script>

<template>
  <p>縦が{{ height }}、横が{{ width }}の長方形の面積は{{ area }}</p>
  <button v-on:click="change">値を変更</button>
</template>
