<template>
    <select v-model="selectedSortOption">
        <option v-for="option in sortOptions" :key="option.value" :value="option.value" data-test="sort-option"
            :class="{ selected: selectedSortOption === option.value }"
            @click="handleChange">
            {{ option.label }}
        </option>
    </select>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits(['sort-change']);

const selectedSortOption = ref('price-asc');

const sortOptions = [
    { value: 'price-asc', label: 'Price: Low to High' },
    { value: 'price-desc', label: 'Price: High to Low' },
    { value: 'rating-desc', label: 'Rating: High to Low' },
];

function handleChange() {
    emit('sort-change', selectedSortOption.value);
}
</script>

<style scoped>
.selected {
    font-weight: bold;
    color: blue;
}
</style>