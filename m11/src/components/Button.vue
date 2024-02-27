<script setup>
const props = defineProps(['sign'])
const first = 5
const second = 7

</script>

<template>
    <button @click="$emit('click')">{{ sign }}</button>
</template>

<style scoped>
button{
    background-color: #2b67a3;
    color: #ffffff;
    font-size: 20px;
}
</style>