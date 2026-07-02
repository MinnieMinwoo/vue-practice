<script setup lang="ts">
import { ref, watch } from 'vue'

interface Cocktail {
  id: number
  name: string
  price: number
}

const cocktailNo = ref(1)
const priceMsg = ref('')
watch(cocktailNo, () => {
  priceMsg.value = getCocktailInfo(cocktailNo.value)
})

const getCocktailInfo = (cocktailNo: number): string => {
  const cocktailDataListInit = new Map<number, Cocktail>()
  cocktailDataListInit.set(1, { id: 1, name: 'ホワイトレディ', price: 1200 })
  cocktailDataListInit.set(2, { id: 2, name: 'ブルーハワイ', price: 1500 })
  cocktailDataListInit.set(3, { id: 3, name: 'ニューヨーク', price: 1100 })
  cocktailDataListInit.set(4, { id: 4, name: 'マティーニ', price: 1500 })

  const cocktail = cocktailDataListInit.get(cocktailNo)
  if (cocktail === undefined) return '該当カクテルはありません'
  return `該当カクテルは${cocktail.name}で値段は${cocktail.price}円です。`
}

setInterval(() => {
  cocktailNo.value = Math.round(Math.random() * 3) + 1
}, 1000)
</script>

<template>
  <p>現在のカクテル番号: {{ cocktailNo }}</p>
  <p>{{ priceMsg }}</p>
</template>
