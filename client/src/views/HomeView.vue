<script setup lang="ts">
import dayjs from 'dayjs';

import { ref } from 'vue';

import LayoutBase from '@/components/LayoutBase.vue';
import Countdown from '@/components/Countdown.vue';

const targetDate = ref(new Date(2025, 3, 4, 12, 0, 0))
</script>

<template>
  <LayoutBase>
    <div class="flex flex-col gap-6 justify-center">
      <h1 class="text-black text-center font-bold text-2xl sm:text-3xl md:text-3xl lg:text-5xl">KORBEN DALLAS COUNTRY CLUB</h1>
      <Countdown :targetDate="dayjs(targetDate)"></Countdown>
    </div>
  </LayoutBase>
</template>
