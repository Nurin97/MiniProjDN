<template>
    <div class="background">
        <h1>Birthday Reminder</h1>
        <form @submit.prevent="addBirthday">
            <input v-model="name" placeholder="Name" required />
            <input v-model="date" type="date" required />
            <button type="submit">Add Birthday</button>
        </form>
            <ul>
            <li v-for="(b, index) in birthdays" :key="index">
                {{ b.name }} - {{ b.date }}
            <button @click="removeBirthday(index)">Delete</button>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const name = ref('')
const date = ref('')
const birthdays = ref([])

function addBirthday() {
    birthdays.value.push({ name: name.value, date: date.value })
    name.value = ''
    date.value = ''
}

function removeBirthday(index) {
    birthdays.value.splice(index, 1)
}
</script>

<style >

body, html {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
    overflow-x: hidden;
}

.background {
    background-image: url('/src/assets/FieldBg.jpeg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    height: 100vh;
    width: 100vw;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}


form {
    margin-bottom: 1em;
}
input {
    margin-right: 0.5em;
}
button {
    margin-left: 0.5em;
}
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>