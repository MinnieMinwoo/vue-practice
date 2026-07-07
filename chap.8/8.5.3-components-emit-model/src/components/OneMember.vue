<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  id: number
  name: string
  email: string
  points: number
  note?: string
}

interface Emits {
  (event: 'update:points', id: number): void
}

const props = withDefaults(defineProps<Props>(), {
  note: '--',
})
const emit = defineEmits<Emits>()

const localNote = computed(() => props.note)

const onInput = (event: Event) => {
  const element = event.target
  if (!(element instanceof HTMLInputElement)) return

  const inputPoints = Number(element.value)
  emit('update:points', inputPoints)
}
</script>

<template>
  <section class="box">
    <h4>{{ name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>{{ id }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ email }}</dd>
      <dt>保有ポイント</dt>
      <dd>
        <input type="number" v-bind:value="points" v-on:input="onInput" />
      </dd>
      <dt>備考</dt>
      <dd>{{ localNote }}</dd>
    </dl>
  </section>
</template>

<style scoped>
.box {
  border: green 1px solid;
  margin: 10px;
}
</style>
