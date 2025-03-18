<script setup>
import NavBase from './NavBase.vue';
import InstagramIcon from './icons/InstagramIcon.vue';
</script>

<template>
    <div class="layout w-screen h-dvh flex flex-col gap-6 text-orange-300">
        <header class="bg-black p-3 flex sm:text-lg md:text-xl">
            <NavBase></NavBase>
        </header>
        <main class="p-1.5 w-screen h-full flex justify-center">
            <slot></slot>
        </main>
        <footer class="bg-black p-3 flex flex-row justify-center mt-auto">
            <a>
                <InstagramIcon></InstagramIcon>
            </a>
        </footer>
    </div>
</template>