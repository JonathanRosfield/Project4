<script setup>
import {ref, defineProps, defineEmits} from 'vue'

// Categories
const props = defineProps({
    contacts: Array
});

// Categories list 
const categories = ref(['Family', 'Friends', 'Work']);

const emit = defineEmits(['categorySelected']);

// Handle selecting a category
const selectCategory = (category) => {
  console.log('Selected Category:', category);
  emit('categorySelected', category);
};


</script>

<template>
<div class="category-manager">
    <h3>Select a Category for your Contact</h3>
    <div>
        <button class="category-family" @click="selectCategory('Family')">Family</button>
        <button class="category-friends" @click="selectCategory('Friends')">Friends</button>
        <button class="category-work" @click="selectCategory('Work')">Work</button>
    </div>
</div>

</template>