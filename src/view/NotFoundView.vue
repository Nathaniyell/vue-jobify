<script setup>
import {RouterLink} from "vue-router"
</script>

<template>

<section class="text-center flex flex-col justify-center items-center h-96">
      <i class="pi pi-exclamation-triangle text-yellow-700 text-4xl"></i>
      <h1 class="text-4xl mt-4 font-bold mb-4">404 Not Found</h1>
      <p class="text-xl mb-5">This page does not exist</p>
      <RouterLink
        to="/"
        class="text-white bg-violet-700 hover:bg-violet-900 rounded-md px-3 py-2 mt-4"
        >Go Back</RouterLink
      >
    </section>

</template>