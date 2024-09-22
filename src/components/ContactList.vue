<script setup>
import { defineProps } from 'vue';
import DeleteContact from './DeleteContact.vue';


// contacts array 
const props = defineProps({
  contacts: Array
});

// contact deletion
const handleContactDelete = (index) => {
    props.contacts.splice(index, 1);
};

</script>


<template>
 <div id="contact-list">
    <h2>Contact List</h2>
    <ul id="contactList">
        <li v-for="(contact, index) in contacts" :key="index">
            <span>{{ contact.name }} - {{ contact.phone }} ({{ contact.category }})</span>
            <DeleteContact @contactDeleted="handleContactDelete(index)" />
        </li>
    </ul>
 </div>
</template>