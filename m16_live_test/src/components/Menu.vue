<script setup>
import { ref } from 'vue'
import { defineProps } from 'vue'
import { useRouter } from 'vue-router'

const props = defineProps()

const router = useRouter()

const menuItems = ref([
  { id: 1, name: 'Coffee' },
  { id: 2, name: 'Tea' },
  { id: 3, name: 'Sandwich' },
  { id: 4, name: 'Cake' }
])

const showAlert = (itemName) => {
  alert(`You selected: ${itemName}`)
}
</script>

<template>
    <div>
      <h1>Menu</h1>
      <ul>
        <li v-for="item in menuItems" :key="item.id">
          <button @click="showAlert(item.name)">{{ item.name }}</button>
        </li>
      </ul>
    </div>
</template>
  

  