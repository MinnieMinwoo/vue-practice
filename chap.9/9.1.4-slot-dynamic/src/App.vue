<script setup lang="ts">
import { ref } from 'vue'
import OneSection from './components/OneSection.vue'

const tartProblemsInit = ['田はが通じません。', '留守です。']
const taro = ref('田中太郎')
const taroProblems = ref(tartProblemsInit)
const jiro = ref('鈴木次郎')
</script>

<template>
  <section>
    <h2>Slotの利用</h2>
    <OneSection v-bind:name="taro">
      <ul>
        <li v-for="problem in taroProblems" v-bind:key="problem">
          {{ problem }}
        </li>
      </ul>
    </OneSection>
    <OneSection v-bind:name="jiro" />
  </section>
</template>

<style scoped></style>
