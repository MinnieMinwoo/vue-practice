<script setup lang="ts">
import { reactive } from 'vue'

const memberInfo = reactive({
  name: '田中太郎',
  state: '問題ありません。',
})
</script>

<template>
  <section>
    <slot v-bind:memberInfo="memberInfo">
      <p>{{ memberInfo.name }}さんの状況</p>
      <p>{{ memberInfo.state }}</p>
    </slot>
  </section>
</template>
