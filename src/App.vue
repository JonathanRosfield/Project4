<script setup>
import {ref} from 'vue';
import Header from './components/Header.vue';
import ContactForm from './components/ContactForm.vue';
import ContactList from './components/ContactList.vue';

const contacts = ref([]);

// New contact addition
const handleContactAdded = (contact) => {
  contacts.value.push(contact);
};



</script>

<template>
<Header></Header>
<div class="container">
    <ContactForm @contactAdded="handleContactAdded" />
    <ContactList :contacts="contacts" />
  </div>



</template>
