<script setup lang="ts">
import { ref } from 'vue';
import Input from './components/Input.vue';
import Radio from './components/Radio.vue';
import Select from './components/Select.vue';


const currentComponent = ref(Input);
const currentComponentName = ref('Input');
const componentList = [Input, Radio, Select];
const componentNameList = ['Input', 'Radio', 'Select'];

let currnetComponentIndex = 0;
const switchComponent = () => {
  currnetComponentIndex++;
  if (currnetComponentIndex >= componentList.length)
    currnetComponentIndex = 0;
  
  currentComponent.value = componentList[currnetComponentIndex] ?? Input;
  currentComponentName.value = componentNameList[currnetComponentIndex] ?? "Input";
}

</script>
  
<template>
  <p>コンポーネント名: {{ currentComponentName }}</p>
  <KeepAlive>
    <component v-bind:is="currentComponent" />
  </KeepAlive>
  <button v-on:click="switchComponent">切り替え</button>
</template>

<style scoped></style>
