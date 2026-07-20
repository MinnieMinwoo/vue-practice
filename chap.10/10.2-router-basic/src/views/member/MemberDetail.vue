<script setup lang="ts">
import {computed, inject} from 'vue';
import type { Member } from "../../interfaces";

interface Props {
  id: number;
}

const props = defineProps<Props>();
const memberList = inject<Map<number, Member>>('memberList');
const member = computed(() => memberList?.get(props.id) as Member);
console.log('props.id', props.id);
console.log('memberList', memberList);
console.log('member.value', member.value);

const localNote = computed(() => {
  if (!member.value) return '--';
  return member.value.note;
})
</script>

<template>
  <section>
    <h2>会員詳細情報</h2>
    <dl>
      <dt>ID</dt>
      <dd>{{ props.id }}</dd>
      <dt>名前</dt>
      <dd>{{ member.name }}</dd>
      <dt>メールアドレス</dt>
      <dd>{{ member.email }}</dd>
      <dt>保有ポイント</dt>
      <dt>備考</dt>
      <dd>{{ localNote }}</dd>
    </dl>
  </section>
</template>
