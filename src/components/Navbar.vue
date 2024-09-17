<script setup>
import {RouterLink, useRoute} from "vue-router"



const isActiveLink = (routePath) =>{
    const route = useRoute()
    return route.path === routePath
}
</script>


<template>
  <nav class="bg-violet-700 border-b border-violet-500">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="flex h-20 items-center justify-between">
        <div class="flex flex-1 items-center justify-between md:items-stretch md:justify-between">
          <!-- Logo -->
          <RouterLink class="block text-white text-2xl font-bold ml-2" to="/">

            Vue JOBify

          </RouterLink>
          <div class="md:ml-auto">
            <div class="flex space-x-2">
              <RouterLink to="/"
                :class="[isActiveLink('/')? 'bg-violet-900': 'hover:bg-gray-900 hover:text-white','text-white', 'py-2', 'px-3', 'rounded-md']">Home</RouterLink>
              <RouterLink to="/jobs" :class="[isActiveLink('/jobs')? 'bg-violet-900': 'hover:bg-gray-900 hover:text-white','text-white', 'py-2', 'px-3', 'rounded-md']">Jobs</RouterLink>
              <RouterLink to="/jobs/add" :class="[isActiveLink('/jobs/add')? 'bg-violet-900': 'hover:bg-gray-900 hover:text-white','text-white', 'py-2', 'px-3', 'rounded-md']">Add Job</RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>