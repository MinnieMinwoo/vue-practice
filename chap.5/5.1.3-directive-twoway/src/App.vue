<script setup lang="ts">
import { ref } from 'vue'

const inputName2Way = ref('双方向')
const onInputName2Way = (event: Event) => {
  if (!(event.target instanceof HTMLInputElement)) return
  const element: HTMLInputElement = event.target
  inputName2Way.value = element.value
}
</script>

<template>
  <section>
    <input type="text" v-bind:value="inputName2Way" v-on:input="onInputName2Way" />
    <p>{{ inputName2Way }}</p>
  </section>
</template>
