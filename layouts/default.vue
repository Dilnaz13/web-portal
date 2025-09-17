<template>
    <header class = "z-[1100] flex flex-row text-teal-500 font-bold w-full items-center relative bg-teal-50 border-b-2 border-teal-400
    max-sm:justify-between max-sm:relative p-2">
        <div class = "basis-1/4 items-center justify-start px-8 min-w-40 max-sm:basis-auto">
            <img src="assets/images/plant.png" class = "w-20 h-18 bg-transparent">
        </div>
        <div class = "basis-1/4 max-sm:basis-auto">
        </div>
        <nav :class = "{'z-[1200] basis-1/2 flex flex-row items-center justify-end px-8 gap-4': !burger || burger,
        'max-sm:basis-auto max-sm:absolute max-sm:top-full max-sm:w-full max-sm:justify-center max-sm:gap-0 max-sm:bg-white max-sm:px-0': burger,
        'max-sm:hidden': !burger}">
            <NuxtLink to = "/" class = "my-auto p-2 hover:bg-teal-500 hover:text-white max-sm:w-full max-sm:border-b-2
            max-sm:border-black max-sm:text-center">Координаты</NuxtLink>
            <div class = "relative my-auto p-2 hover:bg-teal-500 hover:text-white max-sm:w-full max-sm:text-center cursor-pointer" @click = "switch_submenu">Гидрология
              <div class="flex flex-col absolute left-0 top-full bg-white text-teal-500 w-56 text-center max-sm:relative max-sm:w-full
              max-sm:bg-teal-50 max-sm:text-teal-500" v-show = "submenu">
                <NuxtLink to = "/Lab3" class = "p-2 border-b border-teal-400 hover:bg-teal-500 hover:text-white
                max-sm:w-full max-sm:border-t-2 max-sm:text-center"@click = "submenu = false">Уровень воды</NuxtLink>
                <NuxtLink to = "/Lab4" class = "p-2 border-b border-teal-400 hover:bg-teal-500 hover:text-white
                max-sm:w-full max-sm:border-t-2 max-sm:text-center"@click = "submenu = false">Прозрачность</NuxtLink>
                <NuxtLink to = "/Lab5" class = "p-2 border-b border-teal-400 hover:bg-teal-500 hover:text-white
                max-sm:w-full max-sm:border-t-2 max-sm:text-center"@click = "submenu = false">Температура</NuxtLink>
                <NuxtLink to = "/Lab6" class = "p-2 border-b border-teal-400 hover:bg-teal-500
                hover:text-white max-sm:w-full max-sm:border-t-2 max-sm:text-center"@click = "submenu = false">Электропроводность</NuxtLink>
              </div>
            </div>
            <NuxtLink to = "/inform"
            :class = "{'my-auto p-2 hover:bg-teal-500 hover:text-white max-cm:w-full max-sm:border-b-2 max-sm:border-black max-sm:text-center': submenu,
              'my-auto p-2 hover:bg-teal-500 hover:text-white max-sm:w-full max-sm:border-b-2 max-sm:border-t-2 max-sm:border-black max-sm:text-center': !submenu}">
               Патогены</NuxtLink>
        </nav>
        <div v-if = "!burger" @click = "switch_burger" class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6">
            <span class = "h-[3px] w-full bg-teal-700"></span>
            <span class = "h-[3px] w-full bg-teal-700"></span>
            <span class = "h-[3px] w-full bg-teal-700"></span>
        </div>
        <div v-else class = "max-sm:flex max-sm:flex-col max-sm:mr-8 max-sm:justify-between max-sm:items-center max-sm:w-8 max-sm:h-6" @click = "switch_burger">
            <span class = "h-[3px] w-full bg-teal-700 rotate-45 relative top-[9px]"></span>
            <span class = "h-[3px] w-full bg-teal-700 opacity-0"></span>
            <span class = "h-[3px] w-full bg-teal-700 relative bottom-3 rotate-[-45deg]"></span>
        </div>
    </header>

    <main class = "z-[2] flex p-[4px] h-screen">
        <slot />
    </main>
 
    <footer class = "flex flex-row w-full bg-teal-50 border-t-2 border-teal-400 items-center justify-center px-4 py-2 gap-4">
        <a href = "https://www.youtube.com/"><img src="assets/images/youtube-logo.png" class = "w-16 h-16"></a>
        <a href = "https://github.com/"><img src="assets/images/git.png" class = "w-16 h-16"></a>
        <a href = "https://www.instagram.com/"><img src="assets/images/insta-logo.png" class = "w-16 h-16"></a>
    </footer>
</template>


<script setup lang="ts">
import { useHead } from '#app';
import {ref} from 'vue'


const burger = ref<boolean>(false)
const submenu = ref<boolean>(false)


const switch_burger = ()=> {burger.value = !burger.value}
const switch_submenu = ()=> {submenu.value = !submenu.value}

</script>
