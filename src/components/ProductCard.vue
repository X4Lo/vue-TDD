<template>
    <div class="bg-white shadow-lg rounded-lg overflow-hidden h-full flex flex-col">
        <img :src="product.images[0]" alt="Product Image" class="w-full h-48 object-cover">
        <div class="p-4 flex flex-col flex-grow">
            <div class="flex-grow">
                <h3 class="text-lg font-bold mb-2">{{ product.name }}</h3>
                <p class="text-gray-600 text-sm mb-4">{{ product.description }}</p>
            </div>
            <div class="mt-auto flex justify-between items-center">
                <span class="text-xl font-semibold text-blue-500">${{ product.price }}</span>
                <span class="text-xl font-semibold text-blue-500">{{ product.rating }}</span>
                <button
                    class="bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-4 rounded transition duration-300"
                    @click="handleAddToCart()">add to cart</button>
            </div>
        </div>
    </div>
</template>

<script setup>

const emit = defineEmits(['add-to-cart']);

const { product } = defineProps({
    product: {
        type: Object,
        required: true,
    },
});

const handleAddToCart = () => {
    console.log(product)
    emit('add-to-cart', product)
}

</script>