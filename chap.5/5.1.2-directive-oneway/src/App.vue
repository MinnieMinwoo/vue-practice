<script setup lang="ts">
import { ref } from 'vue'

const inputNameBind = ref('しんちゃん')
const inputNameOn = ref('ななし')
const onInputNmae = (event: Event) => {
  if (!(event.target instanceof HTMLInputElement)) return
  const element: HTMLInputElement = event.target
  inputNameOn.value = element.value
}
</script>

<template>
  <section>
    <input type="text" v-bind:value="inputNameBind" />
  </section>
  <br />
  <section>
    <input type="text" v-on:input="onInputNmae" />
    <p>{{ inputNameOn }}</p>
  </section>
</template>
