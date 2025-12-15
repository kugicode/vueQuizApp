<script setup>
import { ref } from 'vue';
import Questions from './Questions.vue';

const score = ref(0);
const currentQuestionIndex = ref(0);

const questions = [
    {
        question: "What is 2+2!",
        options: ["2", "4", "1", "5"],
        answer: "4" 
    },

    {
        question: "What language is Vue.js built with?",
        options: ["Python", "Java", "Javascript", "None"],
        answer: "Javascript"
    }

];

const clicked = (option) => {
    // console.log("You have clicked");
    if(questions[currentQuestionIndex.value].answer === option){
        console.log("You have got the right answer!");
        score.value++;
    }
    currentQuestionIndex.value++;
}

</script>

<template>
<div v-if="currentQuestionIndex < questions.length">
<Questions 
  :question="questions[currentQuestionIndex]" 
  @option-selected="clicked"                
/>
</div>

<div v-else>
<h2>You got: {{ score }} / {{ questions.length }}</h2>
</div>

</template>