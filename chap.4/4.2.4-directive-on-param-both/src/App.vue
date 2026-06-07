<script setup lang="ts">
import { ref } from 'vue'

const pMessage = ref('イベント前（ここをクリック！）')
const pBgColorEvent = ref('white')
const onPClickWithEvent = (bgColor: string, event: MouseEvent) => {
  pBgColorEvent.value = bgColor
  pMessage.value = event.timeStamp.toString()
}
</script>

<template>
  <p
    v-on:click="onPClickWithEvent('green', $event)"
    v-bind:style="{ backgroundColor: pBgColorEvent }"
  >
    {{ pMessage }}
  </p>
</template>
