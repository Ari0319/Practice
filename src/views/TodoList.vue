<script setup>
let search = $ref('')
let upper = $computed(() => search.toUpperCase())
</script>

<template>
  <p>Your input: {{ search }}</p>
  <p :class="upper === search ? 'green' : 'red'">
    Upper Case: {{ upper }}
  </p>
  <input v-model="search">
  <button @click="search = ''">Clear</button>
</template>

<style scoped>
input { background: #eee; }
.green { color: green; }
.red { color: red; }
</style>
