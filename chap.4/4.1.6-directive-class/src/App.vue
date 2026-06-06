<script setup lang="ts">
import { computed, ref } from 'vue'

type ComputedStylesReturn = {
  textColorRed: boolean
  bgColorBlue: boolean
}

const msg = ref('こんにちは！世界')

const isTextColorRed = ref(true)
const isBgColorBlue = ref(false)

const styles = ref({
  textColorRed: false,
  bgColorBlue: true,
})

const computedStyles = computed((): ComputedStylesReturn => {
  const randomText = Math.round(Math.random())
  const textColorFlag = randomText === 0

  const randomBg = Math.round(Math.random())
  const bgColorFlag = randomBg === 0

  return {
    textColorRed: textColorFlag,
    bgColorBlue: bgColorFlag,
  }
})
</script>

<template>
  <p v-bind:class="{ textColorRed: true, bgColorBlue: true }">{{ msg }}</p>
  <p v-bind:class="{ textColorRed: isTextColorRed, bgColorBlue: isBgColorBlue }">{{ msg }}</p>
  <p v-bind:class="{ textColorPink: true }">{{ msg }}</p>
  <p v-bind:class="{ 'text-color-pink': true }">{{ msg }}</p>
  <p class="textSize24" v-bind:class="{ textColorRed: isTextColorRed, bgColorBlue: isBgColorBlue }">
    {{ msg }}
  </p>
  <p class="textSize24" v-bind:class="styles">{{ msg }}</p>
  <p v-bind:class="computedStyles">{{ msg }}</p>
</template>

<style>
.textColorRed {
  color: red;
}
.text-color-pink {
  color: pink;
}
.bgColorBlue {
  background-color: blue;
}
.textSize24 {
  font-size: 24px;
}
</style>
