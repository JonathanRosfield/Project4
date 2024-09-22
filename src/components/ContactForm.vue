<script setup>
import { ref, defineEmits } from 'vue';

// Selected category
const props = defineProps({
  selectedCategory: String
});

// Define emit for an added contact
const emit = defineEmits(['contactAdded']);

// Define reactive properties
const contactName = ref('');
const contactPhone = ref('');

// Form submission
const onSubmit = () => {
    if (contactName.value && contactPhone.value){
        emit('contactAdded',{
            name: contactName.value,
            phone: contactPhone.value,
            category: props.selectedCategory 
        });

      // Clear the form inputs
      contactName.value = '';
      contactPhone.value = '';
    }


};


</script>


<template>
<div id="contact-form">
    <h2>Add a New Contact</h2>
    <form @submit.prevent="onSubmit">
        <div class="form-control">
            <label for="contactName">Name:</label>
            <input v-model="contactName" type="text" id="contactName" required />
        </div>
        <div class="form-control">
            <label for="contactPhone">Phone Number:</label>
            <input v-model="contactPhone" type="tell" id = "contactPhone" required />
        </div>
        <button type="submit">Add Contact</button>
    </form>
</div>

</template>