<template>
    <input type="text" v-model="name" @change="handleSearchChange" />
    <select :v-model="selectedOption">
        <option value="all" @click="handleChange" data-test="category-option">All Categories</option>
        <option v-for="option in categories" :key="option.id" :value="option.id" data-test="category-option"
            @click="handleChange(option.id)">
            {{ option.name }}
        </option>
    </select>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits(['search-change', 'category-change']);

const name = ref('');
const selectedOption = ref('all');

const props = defineProps({
    categories: {
        type: Array,
        default: () => [],
    },
    selectedCategory: {
        type: String,
        default: 'all',
    },
});

const handleSearchChange = () => {
    emit('search-change', name.value);
};

const handleChange = (value) => {
    selectedOption.value = value;
    emit('category-change', selectedOption.value);
}
</script>