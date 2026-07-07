<script setup lang="ts">
import type { Member } from '../interfaces'
import { computed, inject } from 'vue'

interface Props {
  id: number
}

const props = defineProps<Props>()

const memberList: Map<number, Member> = inject('memberList') ?? new Map()
const member = computed(
  () => memberList.get(props.id) ?? { id: 0, name: '', email: '', points: 0, note: '' },
)

const localNote = computed(() => {
  const localNote = member.value.note
  return localNote ?? '--'
})
</script>

<template>
  <section class="box">
    <h4>{{ member.name }}さんの情報</h4>
    <dl>
      <dt>ID</dt>
      <dd>{{ id }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ member.email }}</dd>
      <dt>保有ポイント</dt>
      <dd>
        <input type="number" v-model.number="member.points" />
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
