<script setup>
import {ref} from 'vue'

const props = defineProps({
  contacts: Array,
});


</script>

<template>
   <div id="favorite-contacts">
    <h2>Favorite Contacts</h2>
    <ul>
      <li v-for="contact in favoriteContacts" :key="contact.phone">
        {{ contact.name }} - {{ contact.phone }}
      </li>
    </ul>
    <p v-if="!favoriteContacts || favoriteContacts.length === 0">No favorite contacts yet.</p>
  </div>
</template>