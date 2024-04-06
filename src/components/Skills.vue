<script setup>
import { computed, defineComponent, reactive, ref } from 'vue';
import { useDisplay } from 'vuetify';

const { xs, sm, md, lg, xlAndUp } = useDisplay();

defineComponent({
    name: 'Skills',
});

const skills = reactive({
    options: [
        {
            id: 1,
            name: 'skills',
        },
        {
            id: 2,
            name: 'experience',
        },
    ],
    items: [
        {
            id: 1,
            option: 1,
            name: 'Canva',
            experience: '3 years',
        },
        {
            id: 2,
            option: 1,
            name: 'Figma',
            experience: '2 years',
        },
        {
            id: 3,
            option: 1,
            name: 'Microsoft Office',
            experience: '5 years',
        },
        {
            id: 4,
            option: 1,
            name: 'Adobe PhotoShop',
            experience: '3 months',
        },
        {
            id: 5,
            option: 1,
            name: 'MySQL',
            experience: '1 years',
        },
        {
            id: 6,
            option: 2,
            name: 'Ketua Osis Smpn 1 Pangkalan Kerinci',
            experience: '2018-2019',
        },
        {
            id: 7,
            option: 2,
            name: 'Purna Paskibraka Muda',
            experience: '2020',
        },
        {
            id: 8,
            option: 2,
            name: 'Purna Paskibraka Kab Pelalawan',
            experience: '2021',
        },
        {
            id: 9,
            option: 2,
            name: 'Wakil Ketua MPK SMAN 2 Pangkalan Kerinci',
            experience: '2020-2021',
        },
        {
            id: 10,
            option: 2,
            name: 'Juara PBB Tingkat Nasional',
            experience: '2018',
        },
    ],
});

const activeOption = ref(null);

const skillItems = computed(() =>
    activeOption.value != null ? skills.items.filter((item) => item.option === activeOption.value) : skills.items,
);

const toggleOption = (option) => (activeOption.value = activeOption.value === option.id ? null : option.id);
</script>
<template>
    <div class="experience-skills">
        <h5 class="text-h5 text-uppercase text-center text-deep-purple-accent-1">Experience skills</h5>
        <v-slide-group show-arrows center-active class="mt-3">
            <v-slide-group-item v-for="option in skills.options" :key="option.id" v-slot="{ isSelected, toggle }">
                <v-btn
                    class="ma-2"
                    rounded
                    :color="option.id === activeOption ? 'deep-purple-accent-1' : undefined"
                    @click="toggleOption(option)"
                >
                    {{ option.name }}
                </v-btn>
            </v-slide-group-item>
        </v-slide-group>
        <v-item-group selected-class="bg-deep-purple-accent-1" class="technical-skills__row">
            <v-row>
                <v-col
                    v-for="skill in skillItems"
                    :key="skill.id"
                    :cols="xs ? 12 : sm ? 6 : md || lg ? 4 : xlAndUp ? 3 : undefined"
                >
                    <v-item v-slot="{ isSelected, selectedClass, toggle }">
                        <v-card :class="['technical-skills__item', selectedClass]" @click="toggle">
                            <div class="text-h5 text-center">{{ isSelected ? skill.experience : skill.name }}</div>
                        </v-card>
                    </v-item>
                </v-col>
            </v-row>
        </v-item-group>
    </div>
</template>

<style scoped>
.experience-skills__row {
    display: flex;
    margin-top: 24px;
}

.experience-skills__item {
    display: flex;
    flex: 0 1 25%;
    align-items: center;
    justify-content: center;
    text-align: center;
    height: 80px;
    user-select: none;
}
</style>
