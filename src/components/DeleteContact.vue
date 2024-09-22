<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['contactDeleted']);

// Deletion function
const handleDelete = () => {
    emit('contactDeleted');
};


</script>

<template>
  <button class="delete-button" @click="handleDelete">Delete</button>

</template>