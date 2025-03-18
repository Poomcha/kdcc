<script setup>
import dayjs, { Dayjs } from 'dayjs';
import duration from 'dayjs/plugin/duration';

import { ref, onMounted, watch } from 'vue';

dayjs.extend(duration);

const props = defineProps({
    targetDate: {
        type: Dayjs,
        required: true,
    },
})

const days = ref(0);
const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

const updateCountdown = () => {
    const now = dayjs();
    const diff = dayjs(props.targetDate).diff(now);
    const duration = dayjs.duration(diff);

    days.value = Math.floor(duration.asDays());
    hours.value = duration.hours();
    minutes.value = duration.minutes();
    seconds.value = duration.seconds();
};

onMounted(() => {
    updateCountdown();
    setInterval(updateCountdown, 1000);
})

watch(() => props.targetDate, () => {
    updateCountdown();
});

const countdownContainerClass = "flex flex-col gap-1.5 lg:gap-3 border-3 lg:border-5 p-1.5 lg:p-3 w-15 lg:w-30"

</script>

<template>
    <div class="flex gap-3 sm:gap-6 md:gap-9 text-black justify-center font-bold text-xl sm:text-2xl lg:text-3xl">
        <div :class="countdownContainerClass">
            <p class="text-center">D</p>
            <hr class="h-1 border-t-3 lg:border-t-5">
            <p class="text-center">{{ days }}</p>
        </div>
        <div :class="countdownContainerClass">
            <p class="text-center">H</p>
            <hr class="h-1 border-t-3 lg:border-t-5">
            <p class="text-center">{{ hours }}</p>
        </div>
        <div :class="countdownContainerClass">
            <p class="text-center">M</p>
            <hr class="h-1 border-t-3 lg:border-t-5">
            <p class="text-center">{{ minutes }}</p>
        </div>
        <div :class="countdownContainerClass">
            <p class="text-center">S</p>
            <hr class="h-1 border-t-3 lg:border-t-5">
            <p class="text-center">{{ seconds }}</p>
        </div>
    </div>
</template>