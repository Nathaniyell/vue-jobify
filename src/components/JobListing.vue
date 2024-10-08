<script setup>
import { defineProps, computed, ref } from "vue";
import { RouterLink } from "vue-router";

const props = defineProps({
  job: {
    type: Object,
    required: true, // Ensure that job is passed as a required prop
  },
});

const showFullDescription = ref(false);

const truncatedDescription = computed(() => {
  let description = props.job?.description || "No description available"; // Fallback in case description is missing

  if (!showFullDescription.value && description.length > 100) {
    description = description.substring(0, 100) + "...";
  }

  return description;
});

const toggleDescriptionLength = () => {
  showFullDescription.value = !showFullDescription.value;
};
</script>

<template>
  <div class="bg-white rounded-xl shadow-md relative">
    <div class="p-4">
      <div class="mb-6">
        <div class="text-gray-600 my-2">{{ job?.type || "N/A" }}</div>
        <h3 class="text-xl font-bold">{{ job?.title || "No title available" }}</h3>
      </div>

      <div class="mb-5">
        <p>
          {{ truncatedDescription }}
        </p>
        <button
          class="text-violet-500 hover:text-violet-600 mb-5"
          @click="toggleDescriptionLength"
        >
          {{ showFullDescription ? "Less" : "More" }}
        </button>
      </div>

      <h3 class="text-violet-500 mb-2">{{ job?.salary || "No salary information" }} / Year</h3>

      <div class="border border-gray-100 mb-5"></div>

      <div class="flex flex-col lg:flex-row justify-between mb-4">
        <div class="text-orange-700 mb-3">
          <i class="pi pi-map-marker text-orange-700 text-lg"></i>
          {{ job?.location || "Location not available" }}
        </div>
        <RouterLink
          :to="'/jobs/' + job?.id"
          class="h-[36px] bg-violet-500 hover:bg-violet-600 text-white px-4 py-2 rounded-lg text-center text-sm"
        >
          Read More
        </RouterLink>
      </div>
    </div>
  </div>
</template>
