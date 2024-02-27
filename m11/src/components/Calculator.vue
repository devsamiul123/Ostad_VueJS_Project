<script setup>
import {ref, reactive} from 'vue'
import Button from './Button.vue';

const first = ref(0)
const second = ref(0)
const result = ref()

</script>

<template>
    <input type="number" v-model="first"><br/>
    <input type="number" v-model="second"><br/>

    <Button sign="+" @click="result = first + second"/>
    <Button sign="-" @click="result = first - second"/>
    <Button sign="x" @click="result = first * second"/>
    <Button sign="÷" @click="result = first / second"/>

    <h2>{{ result }}</h2>
</template>

<style scoped>
* {
    margin: 10px;;
}
input {
    padding: 6px 12px;
    font-size: 20px;
    line-height: 1.5;
    color: #212529;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #ced4da;
    appearance: none;
    border-radius: 4px;
    transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;         
}
input:focus{
    color: #88b6e3;
    background-color: #fff;
    border-color: #86b7fe;
    outline: 0;
    box-shadow: 0 0 0 0.25rem rgb(13 110 253 / 25%);
} 
</style>