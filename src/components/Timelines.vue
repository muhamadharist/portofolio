<script setup>
import { defineComponent, reactive } from 'vue';

defineComponent({
    name: 'Timelines',
});

const timelines = reactive([
    {
        id: 0,
        icon: 'mdi-book-education',
        color: 'cyan lighten-1',
        title: 'SDN 005 MAKMUR',
        position: 'Siswa',
        period: ' 2010 — JUN 2016',
    },
    {
        id: 1,
        icon: 'mdi-book-education',
        color: 'amber darken-1',
        title: 'SMPN 1 Pangkalan Kerinci',
        position: 'Siswa',
        period: '2016 — 2019',
    },
    {
        id: 2,
        icon: 'mdi-book-education',
        color: 'blue-darken-3',
        title: 'SMAN 2 Pangkalan Kerinci',
        position: 'Siswa',
        period: '2019 —2022',
        description: 'Science Major',
    },
    {
        id: 3,
        icon: 'mdi-book-education',
        color: 'blue-grey',
        title: 'Riau Islamic University',
        position: 'Mahasiswa',
        period: '2022 - Now',
        description: 'studying informatics engineering',
    },
]);
</script>

<template>
    <div class="timeline mt-5">
        <h5 class="text-h5 text-uppercase text-center text-deep-purple-accent-1">Education</h5>
        <v-timeline class="mt-5">
            <v-timeline-item
                v-for="timeline in timelines"
                :key="timeline.id"
                :dot-color="timeline.color"
                :icon="timeline.icon"
                size="large"
            >
                <template v-slot:opposite>
                    <div
                        :class="`pt-1 headline font-weight-bold text-button text-${timeline.color}`"
                        v-text="timeline.period"
                    ></div>
                </template>
                <div>
                    <h2 :class="`mt-n1 headline font-weight-light mb-4 text-${timeline.color}`">
                        {{ timeline.title }}
                    </h2>
                    <h5 :class="`text-button text-${timeline.color}`">{{ timeline.position }}</h5>
                    <span class="text-subtitle-2">{{ timeline.description }}</span>
                </div>
            </v-timeline-item>
        </v-timeline>
    </div>
</template>
