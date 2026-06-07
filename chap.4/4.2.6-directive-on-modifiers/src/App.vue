<script setup lang="ts">
import { ref } from 'vue'

const message = ref('まだです！')
const onEnterKey = () => {
  message.value = 'エンターキーが押下されました。'
}
const onRightButtonClick = () => {
  message.value = 'ボタンが右クリックされました。'
}
const onShiftClick = () => {
  message.value = 'シフトを押しながらクリックされました。'
}
</script>

<template>
  <p>
    {{ message }}
  </p>
  <input type="text" v-on:keydown.enter="onEnterKey" /><br />
  <button v-on:click.right="onRightButtonClick">右クリック</button>
  <button v-on:click.shift="onShiftClick">シフトを押しながらクリック</button>
</template>
