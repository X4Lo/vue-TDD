<template>
    <ProductFilter name="ProductFilter" @search-change="handleSearchChange" @category-change="handleCategoryChange" />
    <ProductSort name="ProductSort" @sort-change="handleSortChange" :currenSort />
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 max-w-7xl mx-auto my-12">
        <div class="h-full">
            <ProductCard v-for="product in productStore.filteredProducts" :key="product.id" :product="product" />
        </div>
        <p v-if="productStore.filteredProducts.length == 0" class="text-gray-500 text-center py-10">No products found
        </p>
    </div>
</template>

<script setup>
import ProductCard from '../components/ProductCard.vue';
import ProductFilter from '../components/ProductFilter.vue';
import ProductSort from '../components/ProductSort.vue';
import { useProductStore } from '../stores/productStore.js';

const productStore = useProductStore();
console.log(productStore.filteredProducts)

const handleSortChange = (newSortOption) => {
    productStore.setSortOption(newSortOption);
}

const handleSearchChange = (term) => {
    productStore.setSearchQuery(term);
}

const handleCategoryChange = (newCategory) => {
    productStore.setCategory(newCategory);
}
</script>