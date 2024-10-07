<script setup lang="ts">
import TestComponent from '@/components/TestComponent.vue';
import { ref, type Ref, computed } from 'vue';

const username: string = 'Alex';
const userRole: Ref<string> = ref('admin');
const fruits: string[] = ['Apple', 'Banana', 'Orange', 'Grapes'];

const inputValue = ref('Starting Value');

const htmlContent = computed(() => {
  return `<p style="color:red;"> ${inputValue.value}</p>`;
});

const counter = ref(0);
const incrementCounter = () => {
  counter.value++
};
</script>

<template>
  <main>
    Hello world!
  </main>
  <h1>This is main header</h1>
  {{ username }}
  <TestComponent username="username" v-bind:age="22">
    <p>This is a description</p>
    <template v-slot:description>This is another description</template>
  </TestComponent>
  <p v-if="userRole === 'admin'">You are an Admin</p>
  <p v-else-if="userRole === 'user'">You are a regular User</p>
  <p v-else>You are a guest</p>

  <li v-for="(fruit,index) in fruits" :key="index">{{ index + 1 }}. {{  fruit }}</li>

  <!-- <input
  v-bind:value="inputValue"
  v-on:input="(event) =>(inputValue = (event.target as HTMLInputElement).value)"
  /> -->

  <input v-model="inputValue"/>
  <div v-html="htmlContent"></div>
  <h3 v-on:click="incrementCounter">You have click on me {{ counter }} times.</h3>
</template>
