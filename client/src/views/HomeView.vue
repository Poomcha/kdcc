<script setup lang="ts">
import dayjs from 'dayjs';

import { ref } from 'vue';

import LayoutBase from '@/components/LayoutBase.vue';
import Countdown from '@/components/Countdown.vue';

const targetDate = ref(new Date(2025, 3, 4, 12, 0, 0))
</script>

<template>
  <LayoutBase>
    <div class="p-3 sm:p-9 flex flex-col gap-3 sm:gap-9 justify-center backdrop-blur-xs bg-black/5 border border-black/10 shadow-[0_0_15px_rgba(0,0,0,0.5)] text-shadow">
      <h1 class="text-black text-center font-[rubik] font-bold text-3xl sm:text-4xl md:text-5xl lg:text-6xl">KORBEN DALLAS COUNTRY CLUB</h1>
      <Countdown :targetDate="dayjs(targetDate)"></Countdown>
    </div>
  </LayoutBase>
</template>
