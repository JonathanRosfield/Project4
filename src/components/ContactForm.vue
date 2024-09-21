<script setup>





</script>


<template>
<div id="contact-form">
    <h2>Add a New Contact</h2>
    <form @submit.prevent="onSubmit">
        <div class="form-control"></div>
            <label for="contactName">Name:</label>
            <input v-model="contactName" type="text" id="contactName" required />
        </div>
        





</template>