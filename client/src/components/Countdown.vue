<script setup>
import dayjs, { Dayjs } from 'dayjs';
import duration from 'dayjs/plugin/duration';

import { ref, onMounted, watch } from 'vue';

const pad = (n) => n.toString().padStart(2, "0");

dayjs.extend(duration);

const props = defineProps({
    targetDate: {
        type: Dayjs,
        required: true,
    },
})

const days = ref("0");
const hours = ref("0");
const minutes = ref("0");
const seconds = ref("0");

const updateCountdown = () => {
    const now = dayjs();
    const diff = dayjs(props.targetDate).diff(now);
    const duration = dayjs.duration(diff);

    days.value = pad(Math.floor(duration.asDays()));
    hours.value = pad(duration.hours());
    minutes.value = pad(duration.minutes());
    seconds.value = pad(duration.seconds());
};

onMounted(() => {
    updateCountdown();
    setInterval(updateCountdown, 1000);
})

watch(() => props.targetDate, () => {
    updateCountdown();
});

const countdownContainerClass = "flex flex-col gap-1.5 lg:gap-3 border-3 lg:border-5 p-1.5 lg:p-3 w-15 lg:w-30 shadow-[0_0_5px_rgba(0,0,0,0.25)]"
const countdownSeparatorClass = "h-1 border-t-3 lg:border-t-5 shadow-[0_0_5px_rgba(0,0,0,0.25)]";
</script>

<template>
    <div class="flex gap-1.5 sm:gap-6 md:gap-9 text-black justify-center font-bold text-2xl sm:text-3xl lg:text-4xl">
        <div :class="countdownContainerClass">
            <p class="text-center">D</p>
            <hr :class="countdownSeparatorClass">
            <p class="text-center">{{ days }}</p>
        </div>
        <div :class="countdownContainerClass">
            <p class="text-center">H</p>
            <hr  :class="countdownSeparatorClass">
            <p class="text-center">{{ hours }}</p>
        </div>
        <div :class="countdownContainerClass">
            <p class="text-center">M</p>
            <hr  :class="countdownSeparatorClass">
            <p class="text-center">{{ minutes }}</p>
        </div>
        <div :class="countdownContainerClass">
            <p class="text-center">S</p>
            <hr  :class="countdownSeparatorClass">
            <p class="text-center">{{ seconds }}</p>
        </div>
    </div>
</template>