<script setup>
import {ref} from 'vue';
import Header from './components/Header.vue';
import ContactForm from './components/ContactForm.vue';
import ContactList from './components/ContactList.vue';
import CategoryManager from './components/CategoryManager.vue';
import DeleteContact from './components/DeleteContact.vue';

const contacts = ref([]);

// New contact addition
const handleContactAdded = (contact) => {
  contact.category = selectedCategory.value || 'Uncategorized'; 
  contacts.value.push(contact);
};

// Category selection 
const selectedCategory = ref(null);
const handleCategorySelected = (category) => {
  selectedCategory.value = category;
};

</script>

<template>
<Header></Header>
<div class="container">
    <CategoryManager @categorySelected="handleCategorySelected" />
    <ContactForm :selectedCategory="selectedCategory" @contactAdded="handleContactAdded" />
    <ContactList :contacts="contacts" />
  </div>



</template>
