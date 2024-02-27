<script setup>
import Calculator from './components/Calculator.vue'
import Anime from './components/Anime.vue'
</script>

<template>
  <div class="anime">
    <Anime />
  </div>
  <div>
    <h1>Calculator</h1>
    <Calculator/>
  </div>
</template>

<style scoped>
div{
  display: inline-block;
  margin: 20px;
}
.anime{
  max-width: 25%;
}
</style>
