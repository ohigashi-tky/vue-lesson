<script setup>
import { ref, computed, watch, watchEffect } from 'vue'

const message = ref('<h1>Hello</h1>')
const vueURL = ref('https://vuejs.org')
const vueId = ref('vue-link')
const count = ref(0)
const count1 = ref(0)
const count2 = ref(0)
const count3 = ref(0)
function countUp(event, times) {
  count.value++
}
const eventName = 'keyup'
const userInput = ref('')
const score = ref(0)
const evaluation = computed(() => {
  return score.value > 3 ? 'Good' : 'Bad'
})
watchEffect(() => {
  // console.log('watchEffect')
  // console.log(count.value)
  // setTimeout(() => {
  //   console.log('after 1 second')
  // }, 1000)
})
watch(count1, (newValue, oldValue) => {
  console.log('watch')
  console.log('newValue', newValue)
  console.log('oldValue', oldValue)
})
const isRed = ref(true)
const isBgBlue = ref(true)
function toggleClass() {
  isRed.value = !isRed.value
  isBgBlue.value = !isBgBlue.value
}
const className = ref('red')
</script>
<template>
  <div>Hello</div>
  <div>{{ message }}</div>
  <!-- XSS攻撃の可能性があるのでなるべく使わない -->
  <div v-html="message"></div>
  <br />
  <!-- v-bind→:と省略可 非常に使われる -->
  <a :id="vueId" :href="vueURL">Vue.js</a>
  <!-- 一括v-bind -->
  <a v-bind="{ id: vueId, href: vueURL }">Vue.js</a>
  <button @click="count++">button</button>
  <button @click="countUp($event, 5)">button2</button>
  <p>{{ count }}</p>
  <button @click="$event.preventDefault">button</button>
  <a :href="vueURL" @click="$event.preventDefault()">Vue.js</a>
  <a :href="vueURL" @click="$event.stopPropagation()">Vue.js</a>
  <a :href="vueURL" @click.prevent>Vue.js</a>
  <a :href="vueURL" @click.stop="">Vue.js</a>
  <a :href="vueURL" @click.prevent.stop>Vue.js</a>
  <input type="text" @keyup.space.delete="count++" />
  <p>{{ count }}</p>
  <input type="text" @[eventName].space.delete="count++" />
  <input v-model="userInput" type="text" />
  <p>{{ userInput }}</p>
  <button @click="userInput = 'hi'">button</button>
  <button @click="score++">+1</button>
  <p>{{ score > 3 ? 'Good' : 'Bad' }}</p>
  <p>{{ evaluation }}</p>
  <p>{{ score }}</p>
  <p>{{ count1 }}</p>
  <p>{{ count2 }}</p>
  <p>{{ count3 }}</p>
  <button @click="count1++">count1+1</button>
  <button @click="count2++">count2+1</button>
  <button @click="count3++">count3+1</button>
  <div class="border" :class="{ red: isRed, 'bg-blue': isBgBlue }">Hello</div>
  <div :class="[className, { 'bg-blue': isBgBlue }]">Hello</div>
  <button @click="toggleClass">toggle</button>
  <div :style="{ color: 'red', backgroundColor: 'blue' }">Hello</div>
</template>
<style>
.red {
  color: red;
}
.bg-blue {
  background-color: blue;
}
.border {
  border: solid 1px red;
}
</style>
