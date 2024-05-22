<template>
    <UHeader>
        <template #left>
            <NuxtLink to="/" class="flex items-end gap-2 font-bold text-xl text-gray-900 dark:text-white"
                      aria-label="Nuxt UI"><img src="/image/logo.svg" alt="Compass_logo" class="w-auto h-6">
            </NuxtLink>
            <UAside>
                <UHeaderLinks :links="links"/>
            </UAside>
        </template>
        <template #right>
            <span class="hidden lg:block"> +7 495 118-44-22</span>
            <UButton  color="white" variant="link">Вход</UButton>
            <UButton class="btn-color" variant="solid">Регистрация</UButton>
        </template>

        <template #panel>
            <UNavigationTree :links="links" default-open/>
        </template>
    </UHeader>
</template>

<script setup lang="ts">
const links = [{
    label: 'Тарифы',
    icon: 'i-heroicons-book-open',
    to: '/rates'
}, {
    label: 'Контакты',
    icon: 'i-heroicons-square-3-stack-3d',
    to: '/contacts'
}
]
</script>
