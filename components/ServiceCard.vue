<template>
    <div
        class=" col-span-4 row-span-2 flex flex-col items-center bg-[#FBFCFD] border border-gray-200 rounded-lg shadow md:flex-row hover:bg-gray-100 dark:border-gray-700 dark:bg-gray-800 dark:hover:bg-gray-700 p-5">
        <img :src="icon" alt="icon" />
        <div class="flex flex-col justify-between pl-4 leading-normal">
            <h5 class="mb-2 text-2xl font-bold tracking-tight dark:text-white">{{ title }}</h5>
            <p class="mb-3 font-normal dark:text-gray-400">{{ description }}</p>
        </div>
    </div>

</template>

<script setup lang="ts">
const props = defineProps<{
    title?: string
    description?: string
    icon: string
}>()
const {title, description, icon} = props;
</script>

<style lang="scss" scoped>
h5 {
    color: #1253A2;
    font-size: 18px;
    line-height: 21.6px;
}
p {
    font-size: 15px;
    line-height: 18px;
}
</style>
