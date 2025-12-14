<script setup>
import { ref } from 'vue';

const score = ref(0);
const currentQuestionIndex = ref(0);


const questions = [
    {
        question: "What is 2+2!",
        options: ["2", "4", "1", "5"],
        answer: "2" 
    },

    {
        question: "What language is Vue.js built with?",
        options: ["Python", "Java", "Javascript", "None"],
        answer: "Javascript"
    }
]

</script>

<template>

<h2>{{ questions[currentQuestionIndex].question }}</h2>

<button v-for="option in questions[currentQuestionIndex].options" :key="option">{{ option }}</button>

</template>