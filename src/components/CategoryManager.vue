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

const selectedCategory = ref(null);


</script>

<template>
<div class="category-manager">
    <h2>Select a Category for your Contact</h2>
    <div>
        <button
            v-for="category in categories"
            :key="category"
            @click="selectCategory(category)"
            :class="{ selected: category === selectedCategory }"
        >
          {{ category }} 
        </button>
    </div>
</div>

</template>