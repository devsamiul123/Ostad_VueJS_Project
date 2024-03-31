<script setup>
import { defineProps } from 'vue'
import { useRouter } from 'vue-router'

const props = defineProps()

const router = useRouter()
</script>

<template>
    <div>
      <h1>Welcome to Our Cafe!</h1>
      <router-link to="/menu">
        <button>See Our Menu</button>
      </router-link>
    </div>
</template>
  

  