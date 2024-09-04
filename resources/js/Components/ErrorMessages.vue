<script setup>
defineProps({
    errors : Object
})

</script>

<template>

    <div class="mb-4" v-if="Object.keys(errors).length">
        <p class="text-red-500 text-sm">Something went wrong!</p>

        <ul class="ml-4 list-disc list-inside">
            <li v-for="(error, index) in errors" :key="index" class="text-red-500 text-sm ">{{ error }}</li>
        </ul>

    </div>

</template>

<style scoped>

</style>
