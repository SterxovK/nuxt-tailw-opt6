<template>
    <div class="mt-[85px] mx-auto mb-10">
        <h2 class="text-center">Документы</h2>
    </div>

    <UCarousel v-slot="{ item }" :items="items" :ui="{
            item: 'basis-full md:basis-1/2 lg:basis-1/3' ,
            container:
            'relative w-full lg:max-w-3xl mx-auto grid-cols-12 gap-x-6 overflow-x-auto snap-x snap-mandatory scroll-smooth',
            indicators: {
                wrapper: 'relative bottom-0 mt-4',
                base: 'rounded-full h-3 w-3 ',
                active: 'bg-blue-500 dark:bg-primary-400',
                inactive: 'bg-gray-800 dark:bg-gray-800 mix-blend-overlay',
             },

        }"
               :prev-button="{
                  color: 'gray',
                  icon: 'i-heroicons-arrow-left-20-solid',
                  class: 'left-12'
                }"
               :next-button="{
                  color: 'gray',
                  icon: 'i-heroicons-arrow-right-20-solid',
                  class: 'right-12'
                }"
               arrows
               indicators
               class="rounded-lg overflow-hidden">
        <div
            class="max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow grid content-between"
            draggable="false">
            <NuxtLink :to="{name: 'products-id', params: { id: item.title} }">
                <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
                {{ item.title }}</h5>
            </NuxtLink>
            <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">{{ item.description }}</p>
            <NuxtLink :to="{name: 'products-id', params: { id: item.title} }">
                <UButton label="О сервисе" class="btn-color">
                    Перейти
                </UButton>
            </NuxtLink>
        </div>
    </UCarousel>
</template>

<script setup>
const items = [
    {
        id: 1,
        title: 'Лицензионный договор',
        description: 'Механизм разбрасывания веерного типа приводится в действие от колес тележки, отличается простой и надежной конструкцией, не нуждается в смазке. '
    },
    {
        id: 2,
        title: 'Политика обработки персональных данных',
        description: 'Радиус разброса ПГМ составляет до 3 метров и может регулироваться.'
    },
    {
        id: 3,
        title: 'Информация об оплате',
        description: 'Десятипозиционный переключатель дозировки расположен на ручке тележки и позволяет очень точно регулировать объем рассыпаемого реагента с учетом его массы и фракции.'
    },
    {
        id: 4,
        title: 'Лицензионный договор',
        description: 'Механизм разбрасывания веерного типа приводится в действие от колес тележки, отличается простой и надежной конструкцией, не нуждается в смазке. '
    }
]
</script>

<style lang="scss" scoped>

</style>
