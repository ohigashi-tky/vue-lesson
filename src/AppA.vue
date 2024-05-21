<script setup>
import { ref } from 'vue'

const message = ref('<h1>Hello</h1>')
const vueURL = ref('https://vuejs.org')
const vueId = ref('vue-link')
</script>
<template>
  <div>Hello</div>
  <div>{{ message }}</div>
  <!-- XSS攻撃の可能性があるのでなるべく使わない -->
  <div v-html="message"></div>
  <br />
  <!-- v-bind→:と省略可 非常に使われる -->
  <a :id="vueId" :href="vueURL">Vue.js</a>
</template>
