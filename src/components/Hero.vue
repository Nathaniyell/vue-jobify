<script setup>
import { defineProps } from "vue"

// defineProps({
//     title:String,
//Either of these methods works, one allows you to set a default while the other just allows you to set the type
// })

defineProps({
    title: {
        type: String,
        default: "Become a Vue Dev"
    },
    
    subTitle: {
        type: String,
        default: "Find the Vue job that fits your skills and needs"
    },
    
})
</script>

<template>
    <section class="relative bg-cover bg-center h-64 lg:h-screen grid place-items-center mb-4">
    <div class="absolute inset-0 bg-[url('../assets/images/vue4.jpg')] bg-cover bg-center filter brightness-50"></div>
    <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col items-center">
        <div class="text-center">
            <h1 class="text-4xl font-bold text-white sm:text-5xl md:text-6xl">
                {{title}}
            </h1>
            <p class="my-4 text-xl text-white">
                {{subTitle}}
            </p>
        </div>
    </div>
</section>

</template>