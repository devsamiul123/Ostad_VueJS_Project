<script setup>
    import { ref, onMounted } from 'vue'

    const quoteData = ref(null)

    const fetchQuote = async () => {
    try {
        const response = await fetch('https://animechan.xyz/api/random');
        const data = await response.json();
        quoteData.value = data;
    } catch (error) {
        console.error('Error fetching quote:', error);
    }
    }

    onMounted(fetchQuote)
</script>

<template>
    <div>
        <h2>Anime Quote:</h2>
        <div v-if="quoteData">
        <p><strong>ID:</strong> {{ quoteData.id }}</p>
        <p><strong>Quote:</strong> {{ quoteData.quote }}</p>
        <p><strong>Anime:</strong> {{ quoteData.anime }}</p>
        <p><strong>Character:</strong> {{ quoteData.character }}</p>
        </div>
        <div v-else>
        <p>Loading...</p>
        </div>
        <button @click="fetchQuote">Fetch</button>
    </div>
</template>

<style scoped>
    p{
        font-size: 20px;
    }
    button{
        background-color: #2b67a3;
        color: #ffffff;
    }
</style>
  