<script setup>
import { defineProps } from 'vue'
import { useRouter } from 'vue-router'

const props = defineProps()

const router = useRouter()
</script>

<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
}
</style>
