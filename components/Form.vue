<template>
    <UForm :schema="schema" :state="state" class="space-y-4" @submit="onSubmit">
        <div class="grid grid-cols-12 gap-x-6">
            <UFormGroup label="Номер автомобиля" name="carNumber" class="col-span-12 lg:col-span-7">
                <UInput v-model="state.carNumber"/>
            </UFormGroup>

            <UFormGroup label="Регион" name="region" class="col-span-12 lg:col-span-5">
                <UInput v-model="state.region"/>
            </UFormGroup>
        </div>

        <UFormGroup label="Свидетельство о регистрации ТС" name="certificate">
            <UInput v-model="state.certificate"/>
        </UFormGroup>
        <div class="grid grid-cols-12 gap-x-6">
            <UButton label="Проверить штрафы" color="blue" variant="solid" type="submit"
                     class="col-span-12 lg:col-span-5"
                     :disabled="!state.carNumber || !state.region || !state.certificate">
                <template #trailing>
                    <UIcon name="i-heroicons-arrow-right-20-solid" class="w-5 h-5"/>
                </template>
            </UButton>
            <UButton label="О сервисе" color="blue" variant="outline" class="col-span-12 lg:col-span-7"
                     @click="isOpen = true">
                <template #leading>
                    <svg xmlns="http://www.w3.org/2000/svg" width="32px" height="23px" viewBox="0 0 24 24">
                        <g
                            fill="none"
                            stroke="currentColor" stroke-width="1.5">
                            <path fill="#1253A2" stroke-linecap="round" stroke-linejoin="round" d="m14 12l-3.5 2v-4z"/>
                            <path
                                d="M2 12.708v-1.416c0-2.895 0-4.343.905-5.274c.906-.932 2.332-.972 5.183-1.053C9.438 4.927 10.818 4.9 12 4.9s2.561.027 3.912.065c2.851.081 4.277.121 5.182 1.053S22 8.398 22 11.292v1.415c0 2.896 0 4.343-.905 5.275c-.906.931-2.331.972-5.183 1.052c-1.35.039-2.73.066-3.912.066s-2.561-.027-3.912-.066c-2.851-.08-4.277-.12-5.183-1.052S2 15.602 2 12.708Z"/>
                        </g>
                    </svg>
                </template>
                <template #trailing>
                    <span>(1 мин. 20 сек)</span>
                </template>
            </UButton>
        </div>

    </UForm>
    <span class="form-agreement">Нажимая «Проверить штрафы» вы соглашаетесь с политикой обработки персональных
        данных и
                принимаете
                оферту</span>

    <UModal v-model="isOpen" :ui="{
        width: 'w-full sm:max-w-3xl',
        overlay: { background: 'bg-slate-900/75 dark:bg-gray-800/75'}
    }">
        <div>
            <iframe width="100%" height="555" src="https://www.youtube.com/embed/6sbQjFBH1dA?si=l49C29RhlxBmI-ll"
                    title="YouTube video player" frameborder="0"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
        </div>
    </UModal>

    <UNotifications/>

</template>

<script setup lang="ts">
import {object, string, type InferType} from 'yup'
import type {FormSubmitEvent} from '#ui/types'

const toast = useToast()
const isOpen = ref(false)
const schema = object({
    carNumber: string()
        .matches(/^[АВЕКМНОРСТУХ]\d{3}(?<!000)[АВЕКМНОРСТУХ]{2}$/ui, 'Is not in correct format - А777АА')
        .required('Required'),
    region: string()
        .matches(/[017]?\d{2}/, 'Is not in correct format - 18')
        .required('Required'),
    certificate: string()
        .matches(/^\d{2}\s?[АВЕКМНОРСТУХ]{2}\s?\d{6}$/ui, 'Is not in correct format - 77 АА 123456')
        .required('Required')
})

type Schema = InferType<typeof schema>

const state = reactive({
    carNumber: undefined,
    region: undefined,
    certificate: undefined,
})

async function onSubmit(event: FormSubmitEvent<Schema>) {
    // Do something with event.data
    console.log(event.data)
    toast.add({title: 'Форма отправлена'})
}
</script>
<style scoped>
.form-agreement {
    font-size: 13px;
    line-height: 15.6px;
    color: #8F8F8F;
}

button {
    font-size: 18px;
    line-height: 23.29px;
    padding: 11px 20px 14.73px;

    span {
        font-size: 15px;
        line-height: 19.41px;
        color: #1253A2;
    }
}
</style>
