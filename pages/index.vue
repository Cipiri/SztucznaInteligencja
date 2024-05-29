<script setup>
const searchQuery = ref("nature")
const resultQuery = ref(null)
const arrayData = ref(null)
const loader = ref(false)
const API_KEY = 'LOGxhYVffi3Ysrkg1pBYo0Lr9ouFPTru4cQhSqSfbr7uXQKDa1AtPJNR' // Zamień na swój klucz API Pexels

const searchData = async() => {
    loader.value = true
    await fetch(`https://api.pexels.com/v1/search?query=${searchQuery.value}`, {
        headers: {
            Authorization: API_KEY
        }
    })
    .then(response => response.json())
    .then(data => {
        resultQuery.value = data.photos
        arrayData.value = data.photos
        loader.value = false
        console.log(data)
    })
    .catch(error => {
        console.error('Error fetching data:', error)
        loader.value = false
    })
}

onBeforeMount(async () => {
    await searchData()
});

// Użycie watch do obserwacji resultQuery
watch(resultQuery, (newValue, oldValue) => {
    arrayData.value = newValue
    console.log(newValue); // Wyświetla nową wartość resultQuery.value
    // Możesz tutaj dodać dodatkowe logikę, która ma się wykonać po zmianie wartości
}, {
    deep: true // opcja 'deep' jest przydatna, jeśli obserwowany obiekt jest złożony (np. obiekt lub tablica)
});
</script>

<template>
    <div class="container">
        <div class="search-container">
            <input type="text" v-model="searchQuery">
            <button @click="searchData" v-if="!loader">Wyszukaj</button>
            <button @click="searchData" disabled v-else>Wyszukaj</button>
        </div>
        <div class="cos" v-if="loader">To jest ładowanie danych</div>

        <div class="result" v-else>
            <div v-for="(value, index) in arrayData" :key="index" class="result-item">
                <img v-if="value.src && value.src.medium" :src="value.src.medium" :alt="value.alt || 'Pexels Image'">
                <p v-if="value.alt">{{ value.alt }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap');

body {
    font-family: 'Roboto', sans-serif;
    background-color: #f0f4f8;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    padding: 20px;
    background-color: #f0f4f8;
}

.search-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 30px;
    padding: 20px;
    background: linear-gradient(135deg, #72edf2 10%, #5151e5 100%);
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

input[type="text"] {
    padding: 10px;
    border: 2px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
    margin-bottom: 10px;
    width: 300px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

button {
    padding: 10px 20px;
    background-color: #007BFF;
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.3s ease;

    &:hover {
        background-color: #0056b3;
        transform: scale(1.05);
    }
    
    &:disabled {
        background-color: #cccccc;
        cursor: not-allowed;
    }
}

.cos {
    font-size: 18px;
    color: #555;
    padding: 20px;
    text-align: center;
}

.result {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
}

.result-item {
    flex: 1 1 200px; /* Każdy element ma szerokość 200px i może się rozciągać */
    max-width: 300px;
    text-align: center;
    background-color: #fff;
    padding: 10px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;

    &:hover {
        transform: scale(1.05);
        box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    }

    img {
        max-width: 100%;
        height: auto;
        border-radius: 10px;
    }
    
    p {
        margin-top: 10px;
        font-size: 14px;
        color: #333;
    }
}

h3 {
    span {
        color: green;
    }
}
</style>
