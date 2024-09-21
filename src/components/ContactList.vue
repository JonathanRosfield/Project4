<script setup>
import { defineProps } from 'vue';

// Get the contacts array 
const props = defineProps({
  contacts: Array
});



</script>


<template>
 <div id="contact-list">
    <h2>Contact List</h2>
    <ul v-if="contacts.length > 0">
        <li v-for="contact in contacts" :key="contact.name">
            {{ contact.name }} - {{ contact.phone }}
        </li>
    </ul>
    <p v-else>No contacts available. Please add a contact first</p>
 </div>


</template>