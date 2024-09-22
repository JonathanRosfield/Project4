<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['contactDeleted']);

// Deletion function
const handleDelete = () => {
    emit('contactDeleted');
};


</script>

<template>
 <button @click="handleDelete">Delete</button>



</template>