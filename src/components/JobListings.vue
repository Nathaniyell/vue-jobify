<script setup>
import {reactive, defineProps, onMounted} from "vue"
import JobListing from "./JobListing.vue"
import {RouterLink} from "vue-router"

defineProps({
    limit: Number,
    showButton:{
        type: Boolean,
        default: false
    }
})

const state = reactive({
jobs:[],
isLoading: true
})

onMounted(async()=>{
    try{

        const response = await fetch("api/jobs")
        const data = await response.json()
        state.jobs = data
    }catch(error){
        console.error(error)
    }finally{
        state.isLoading = false
    }
})

</script>

<template>
<section class="bg-fuchsia-50 px-4 py-10">
<div class="container-xl lg:container m-auto">
<h2 class="text-3xl font-bold text-violet-500 mb-6 text-center">Browse Jobs</h2>

<section v-if="state.isLoading" class="text-center text-yellow-600 animate-pulse font-semibold text-3xl mt-4">
    
Loading Jobs...
</section>

<div v-else class="grid grid-cols-1 gap-6 md:grid-cols-3">

    <JobListing v-for="job in state.jobs.slice(0,limit || state.jobs.length)" :key="job.id" :job="job" />

   
</div>
</div>
</section>
<section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
      <RouterLink
        to="/jobs"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
        >View All Jobs</RouterLink
      >
    </section>
</template>



