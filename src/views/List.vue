<script setup>
let content = $ref(''), list = $ref([]) 
</script>

<template>
  <p v-if="content">Your input: {{ content }}</p> 
  <p v-else>You don't have any input</p>
  <input v-model="content">
  <button @click="list.push(content)">Add</button> 
  <p v-for="item in list">{{ item }}</p> 
</template>

<style scoped>
input { background: #eee; }
</style>