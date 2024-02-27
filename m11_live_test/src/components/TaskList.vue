<script setup>
  import { ref } from 'vue'
  import Popup from './Popup.vue'
  
  const tasks = ref([
    { name: 'Task 1', time: 30 },
    { name: 'Task 2', time: 40 },
    { name: 'Task 3', time: 60 },
    { name: 'Task 4', time: 45 },
    { name: 'Task 5', time: 50 }
  ])
  
  const showPopup = ref(false)
  const editedTask = ref(null)
  let editedTaskIndex = null
  
  const editTask = (index) => {
    editedTask.value = { ...tasks.value[index] }
    editedTaskIndex = index
    showPopup.value = true
  }
  
  const updateTask = (updatedTask) => {
    if (editedTaskIndex !== null) {
      tasks.value[editedTaskIndex] = { ...updatedTask }
      closePopup()
    }
  }
  
  const closePopup = () => {
    showPopup.value = false
    editedTask.value = null
    editedTaskIndex = null
  }
</script>

<template>
    <div>
      <h2>Task List</h2>
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <span>{{ task.name }}</span> - <span>{{ task.time }} minutes</span>
          <button @click="editTask(index)">Edit</button>
        </li>
      </ul>
      <Popup v-if="showPopup" :task="editedTask" @update="updateTask" @close="closePopup" />
    </div>
</template>

<style scoped>

</style>
  