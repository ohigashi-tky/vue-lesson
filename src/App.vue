<script setup>
import { ref, reactive } from 'vue'
const title = ref('タイトル！！')
let price = ref(0)
function increment() {
  price.value += 1
  instructor.bio = 'hi'
  instructor.email = 'test@test.com'
}
const info = ref({
  students: 1000,
  rating: 4
})
const instructor = reactive({
  name: 'Tanaka',
  age: 25,
  sns: {
    twitter: '@tanaka_twitter',
    youtube: '@tanaka_youtube'
  },
  email: ref('tanaka@example.com')
})
instructor.bio = 'hello'

const courseInfo = {
  section: ref(10),
  language: ref('Japanese')
}
</script>

<template>
  <h1>Title: {{ title }}</h1>
  <h2>Price: ${{ price }}</h2>
  <button @click="increment">button</button><br />
  <h2>Students: {{ info.students }}</h2>
  <h2>ratio¥ng: {{ info.rating }}</h2>
  <h2>name: {{ instructor.name }}</h2>
  <h2>age: {{ instructor.age }}</h2>
  <h2>bil: {{ instructor.bio }}</h2>
  <h2>twitter: {{ instructor.sns.twitter }}</h2>
  <h2>email: {{ instructor.email }}</h2>
  <h2>Course Info Sections: {{ courseInfo.language.value }}</h2>
</template>

<style scoped>
header {
  line-height: 1.5;
}
</style>
