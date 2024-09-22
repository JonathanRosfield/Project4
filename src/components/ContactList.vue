<script setup>
import { defineProps } from 'vue';
import {ref, defineEmits} from 'vue';

// Get the contacts array 
const props = defineProps({
  contacts: Array
});

// Emit for marking favorites
const emit = defineEmits(['favoriteToggled']);

// Toggle favorite status for a contact
const toggleFavorite = (contact) => {
  emit('favoriteToggled', contact);
};

</script>


<template>
 <div id="contact-list">
    <h2>Contact List</h2>
    <ul v-if="contacts.length > 0">
        <li v-for="contact in contacts" :key="contact.name">
          <span>{{ contact.name }} - {{ contact.phone }} ({{ contact.category }})</span>
        </li>
    </ul>
    <p v-else>No contacts available. Please add a contact first</p>
 </div>


</template>