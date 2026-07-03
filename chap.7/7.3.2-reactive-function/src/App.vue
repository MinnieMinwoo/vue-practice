<script lang="ts">
import { computed, defineComponent, reactive, toRefs } from 'vue'

export default defineComponent({
  name: 'App',
  setup() {
    const data = reactive({
      PI: 3.14,
      radius: Math.round(Math.random() * 10),
    })

    const area = computed(() => data.PI * data.radius ** 2)

    setInterval(() => {
      data.radius = Math.round(Math.random() * 10)
    }, 1000)

    return {
      ...toRefs(data),
      area,
    }
  },
})
</script>

<template>
  <p>半径{{ radius }}の円の面積を円周率{{ PI }}で計算すると、{{ area }}</p>
</template>

<style scoped></style>
