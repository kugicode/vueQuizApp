<script setup>
const props = defineProps(['question']);
const emit = defineEmits(['option-selected']);

const handleOptionClick = (option) => {
emit('option-selected', option);
}

</script>

<template>
<button v-on:click="handleOptionClick(option)" v-for="option in question.options">{{ option }}</button>
</template>