<script setup>
import { ref } from 'vue'
const tasks = ref([
  { name: "Task 1", time: 60},
  { name: "Task 2", time: 75},
  { name: "Task 3", time: 55},
  { name: "Task 4", time: 30},
  { name: "Task 5", time: 20},
])

const isPopup = ref(false)
const isNull = ref(true)
const name = ref('')
const time = ref()
function setData(){
  console.log(name.value)
  const newTask = {
    name : name.value,
    time : time.value,
  }

  tasks.value.push(newTask)

  name.value = ''
  time.value = null
  isNull.value = true
}

function isEmpty(){
  return (name.value == '' || time.value <= 0) ? false : true
}
</script>

<template>
  <div>
    <h1>My Tasks</h1>
  
    <ol>
      <li v-for="(task, index) in tasks" :key="index">{{ task.name }} : {{ task.time }} minutes <button @click="tasks.splice(index, 1)">Delete</button></li>
    </ol>
    <button @click="isPopup = !isPopup">Add</button>

    <div class="overlay" :style="!isPopup ? 'display:none' : 'display:flex' ">
      <form @submit.prevent class="popup">

        <strong v-if="!isNull" style="color: brown;">Please Fill the Right Information</strong><br/><br/>

        <label for="name">Name</label><br/>
        <input type="text" v-model="name"><br/>

        <label for="time">Time</label><br/>
        <input type="number" v-model="time"><br/>

        <input @click="isEmpty() ? [isPopup = false, setData()] : isNull = false" type="submit" value="Add">
      </form>
    </div>
  </div>
</template>

<style scoped>
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5); /* Semi-transparent black overlay */
    justify-content: center;
    align-items: center;
  }

  .popup {
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  }
</style>
