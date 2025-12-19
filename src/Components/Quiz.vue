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

const newClicked = () => {
    console.log("You clicked the restart button");
    currentQuestionIndex.value = 0;
    score.value = 0;
}

</script>

<template>

<div v-if="currentQuestionIndex < questions.length">
    <h4>Question: {{ currentQuestionIndex + 1 }} / {{ questions.length }}</h4>
<Questions 
  :question="questions[currentQuestionIndex]" 
  @option-selected="clicked"                
/>
</div>


<div v-else>
<h2>You got: {{ score }} / {{ questions.length }}</h2>
<button v-on:click="newClicked">Restart</button>
</div>

</template>