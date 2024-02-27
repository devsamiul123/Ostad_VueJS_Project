<script setup>
  import { ref, defineProps, defineEmits, watch } from 'vue'
  
  const props = defineProps({
    task: Object
  })
  
  const emits = defineEmits(['update', 'close'])
  
  const editedTask = ref(null)
  
  watch(() => props.task, (newValue) => {
    editedTask.value = { ...newValue };
  }, { immediate: true })
  
  const updateTask = () => {
    if (editedTask.value) {
      emits('update', editedTask.value);
      closePopup()
    }
  }
  
  const closePopup = () => {
    emits('close')
  }
</script>
  
<template>
    <div class="popup">
      <h3>Edit Task</h3>
      <form @submit.prevent="updateTask">
        <label for="editedName">Name:</label>
        <input type="text" id="editedName" v-model="editedTask.name" required>
  
        <label for="editedTime">Time:</label>
        <input type="number" id="editedTime" v-model.number="editedTask.time" required>
  
        <button type="submit">Update</button>
        <button @click="closePopup">Cancel</button>
      </form>
    </div>
</template>

<style scoped>
  .popup {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    padding: 20px;
    border: 1px solid #ccc;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
</style>
  