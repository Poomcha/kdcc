<script setup>
import NavBase from './NavBase.vue';
import InstagramIcon from './icons/InstagramIcon.vue';
</script>

<template>
    <div class="layout w-screen h-dvh flex flex-col gap-6 text-orange-300 font-[lexend]">
        <header class="bg-black/80 backdrop-blur-3xl p-3 flex sm:text-lg md:text-xl">
            <NavBase></NavBase>
        </header>
        <main class="p-6 w-screen h-full flex justify-center items-center">
            <slot></slot>
        </main>
        <footer class="bg-black/90 backdrop-blur-xs p-3 flex flex-row justify-center mt-auto">
            <a href="https://www.instagram.com/korben_dallas_country_club/" target="_blank">
                <InstagramIcon></InstagramIcon>
            </a>
        </footer>
    </div>
</template>