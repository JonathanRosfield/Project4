<script setup>
import { ref, onMounted } from 'vue';
import Header from './components/Header.vue';
import ContactForm from './components/ContactForm.vue';
import ContactList from './components/ContactList.vue';
import CategoryManager from './components/CategoryManager.vue';

const contacts = ref([]);

// Load contacts from localStorage
const loadContacts = () => {
    const storedContacts = localStorage.getItem('contacts');
    if (storedContacts) {
        contacts.value = JSON.parse(storedContacts);
    }
};

// Save contacts to localStorage
const saveContacts = () => {
    localStorage.setItem('contacts', JSON.stringify(contacts.value));
};

// New contact addition
const handleContactAdded = (contact) => {
    contact.category = selectedCategory.value || 'Uncategorized'; 
    contacts.value.push(contact);
    saveContacts();  // Save after adding
};

// Handle contact deletion
const handleContactDelete = (index) => {
    contacts.value.splice(index, 1);
    saveContacts();  // Save after deletion
};

// Category selection 
const selectedCategory = ref(null);
const handleCategorySelected = (category) => {
    selectedCategory.value = category;
};

// Load contacts on mount
onMounted(loadContacts);
</script>

<template>
    <Header></Header>
    <div class="container">
        <CategoryManager @categorySelected="handleCategorySelected" />
        <ContactForm :selectedCategory="selectedCategory" @contactAdded="handleContactAdded" />
        <ContactList :contacts="contacts" @contactDeleted="handleContactDelete" />
    </div>
</template>
