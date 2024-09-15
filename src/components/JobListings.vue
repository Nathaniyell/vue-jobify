<script setup>
import jobData from "@/jobs.json"
import {ref} from "vue"
import JobListing from "./JobListing.vue"

const jobs = ref(jobData)

</script>

<template>
<section class="bg-fuchsia-50 px-4 py-10">
<div class="container-xl lg:container m-auto">
<h2 class="text-3xl font-bold text-violet-500 mb-6 text-center">Browse Jobs</h2>

<div class="grid grid-cols-1 gap-6 md:grid-cols-3">

    <JobListing v-for="job in jobs" :key="job.id" :job="job" />

   
</div>
</div>
</section>
</template>



