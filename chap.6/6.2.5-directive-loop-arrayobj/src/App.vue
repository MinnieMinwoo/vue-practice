<script setup lang="ts">
import { ref } from 'vue'

interface Cocktail {
  id: number
  name: string
  price: number
}

const cocktailDataListInit: Cocktail[] = [
  { id: 2345, name: 'ホワイトレディ', price: 1200 },
  { id: 4412, name: 'ブルーハワイ', price: 1500 },
  { id: 6792, name: 'ニューヨーク', price: 1100 },
  { id: 8429, name: 'マティーニ', price: 1500 },
]

const cocktailDataList = ref(cocktailDataListInit)
</script>

<template>
  <ul>
    <li v-for="cocktail in cocktailDataList" v-bind:key="cocktail.id">
      {{ cocktail.name }}の値段は{{ cocktail.price }}円
    </li>
  </ul>
</template>
