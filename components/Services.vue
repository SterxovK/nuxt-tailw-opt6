<template>
    <div class="mt-[79px] mx-auto">
        <h2 class="text-center">Плюсы использования сервиса «Компас» для анализа штрафов</h2>

        <ULandingGrid class="mt-[33px] gap-[35px]">
            <ServiceCard v-for="card in ServiceCards" :key=card.id :icon=card.icon :title=card.title
                         :description=card.description></ServiceCard>
        </ULandingGrid>
    </div>

</template>

<script setup>
const ServiceCards = [
    {
        id: 1,
        icon: "/image/icon/Vector.svg",
        title: "Неограниченый автопарк",
        description: "Можно добавить неограниченное кол-во машин и водителей",
    },
    {
        id: 2,
        icon: "/image/icon/2.svg",
        title: "Сокращение затрат до 50%",
        description: "Максимально быстро узнаете о штрафах в автоматическом режиме, тем самым у вас есть время оплатить по скидке",
    },
    {
        id: 3,
        icon: "/image/icon/3.svg",
        title: "Безопасность",
        description: "Данные передаются в зашифрованном виде, они доступны только получателю",
    },
    {
        id: 4,
        icon: "/image/icon/Frame (1).svg",
        title: "Уведомление о погашении",
        description: "Мы оповестим вас о том, что штраф был погашен и соответствующая запись создана в ГИС ГМП",
    },
    {
        id: 5,
        icon: "/image/icon/Frame (2).svg",
        title: "Квитанция об оплате",
        description: "После совершения оплаты банковской картой на Вашу электронную почту придет квитанция об успешной оплате.",
    },
    {
        id: 6,
        icon: "/image/icon/Frame (3).svg",
        title: "Все история сохраняется по каждой машине",
        description: "Вся история штрафов сохраняется по машине и водителю, позволяет анализировать статистику по штрафам",
    }
]

</script>

<style lang="scss" scoped>

</style>
