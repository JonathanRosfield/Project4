<script setup>
import { defineProps } from 'vue';
import {ref, defineEmits} from 'vue';
import DeleteContact from './DeleteContact.vue';


// Get the contacts array 
const props = defineProps({
  contacts: Array
});

// Handle contact deletion
const handleContactDelete = (index) => {
    props.contacts.splice(index, 1);
};

</script>


<template>
 <div id="contact-list">
    <h2>Contact List</h2>
    <ul v-if="contacts.length > 0">
        <li v-for="contact in contacts" :key="contact.name">
          <span>{{ contact.name }} - {{ contact.phone }} ({{ contact.category }})</span>
          <DeleteContact @contactDeleted="handleContactDelete(index)" />
        </li>
    </ul>
    <p v-else>No contacts available. Please add a contact first</p>
 </div>


</template>