<script setup>
import { defineProps, defineEmits } from 'vue';
import DeleteContact from './DeleteContact.vue';

const props = defineProps({
  contacts: Array
});

const emit = defineEmits(['contactDeleted']);

// Handle contact deletion
const handleContactDelete = (index) => {
    emit('contactDeleted', index);
};
</script>

<template>
 <div id="contact-list">
    <h2>Contact List</h2>
    <ul v-if="contacts.length > 0">
        <li v-for="(contact, index) in contacts" :key="contact.name" class="contact-item">
          <span>{{ contact.name }} - {{ contact.phone }} ({{ contact.category }})</span>
          <DeleteContact @contactDeleted="() => handleContactDelete(index)" />
        </li>
    </ul>
    <p v-else>No contacts available. Please add a contact first.</p>
 </div>
</template>

<style scoped>
.contact-item {
  background-color: #c3d3e4; /* Adjust this as needed */
  border: 1px solid #ddd;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
