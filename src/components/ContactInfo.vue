<script setup>
import { defineComponent, reactive } from 'vue';

defineComponent({
    name: 'ContactInfo',
});

defineProps({
    header: String,
});

const data = reactive([
    {
        icon: 'mdi-cellphone-sound',
        title: 'Phone',
        value: '083175410018',
        href: 'tel:083175410018',
        target: null,
    },
    {
        icon: 'mdi-instagram',
        title: 'instagram',
        value: '@muhamadharist__',
        href: 'https://www.instagram.com/muhamadharist__?igsh=eGUxNHN1ems2OW5w',
        target: '_blank',
    },
    {
        icon: 'mdi-gmail',
        title: 'Gmail',
        value: 'muhamadharist2704@gmail.com',
        href: 'muhamadharist2704@gmail.com',
        target: null,
    },
    {
        icon: 'mdi-github',
        title: 'GitHub',
        value: 'muhamadharist',
        href: 'https://github.com/muhamadharist',
        target: '_blank',
    },
]);
</script>

<template>
    <div class="contact-info">
        <h5 class="text-h5 text-uppercase text-deep-purple-accent-1">{{ header }}</h5>
        <div class="contact-info__item mt-3" v-for="(item, i) in data" :key="i">
            <div class="contact-info__icon">
                <v-icon size="x-large">{{ item.icon }}</v-icon>
            </div>
            <div class="contact-info__content">
                <span class="text-uppercase text-button">{{ item.title }}</span>
                <a :href="item.href" :target="item.target">{{ item.value }}</a>
            </div>
        </div>
    </div>
</template>

<style scoped>
.contact-info__item {
    display: flex;
    align-items: flex-end;
}

.contact-info__content {
    display: flex;
    flex-direction: column;
    margin-left: 10px;
}
</style>
