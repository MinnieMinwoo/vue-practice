<script setup lang="ts">
import { ref } from 'vue'

const cocktailListInit: string[] = ['ホワイトレディ', 'ブルーハワイ', 'ニューヨーク']
const cocktailList = ref(cocktailListInit)
</script>

<template>
  <ul v-for="cocktailName in cocktailList" v-bind:key="cocktailName">
    <li>{{ cocktailName }}</li>
  </ul>
  <ul v-for="(cocktailName, index) in cocktailList" v-bind:key="cocktailName">
    <li>{{ cocktailName }}(インデックス{{ index }})</li>
  </ul>
</template>
