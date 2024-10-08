<script setup>
import {reactive, onMounted} from "vue"
import {useRoute, RouterLink, useRouter} from "vue-router"
import BackButton from "@/components/BackButton.vue"
import {useToast} from "vue-toastification"


const route = useRoute()
const router = useRouter()
const toast = useToast()

const jobId = route.params.id

const state = reactive({
  job: {},
  isLoading: true
})

onMounted(async()=>{
    try{

        const response = await fetch(`/api/jobs/${jobId}`)
        const data = await response.json()
        state.job = data
    }catch(error){
        console.error(error)
    }finally{
        state.isLoading = false
    }
})
const deleteJob = async () => {
  const confirm = window.confirm("Are you sure you want to delete this Job?")
  if(confirm){
  try {
    const response = await fetch(`/api/jobs/${jobId}`, {
      method: "DELETE",
      headers: {
        "Content-Type": "application/json",
      },
    });

    // Check if the deletion was successful
    if (response.ok) {
      toast.success("Job Deleted Successfully");
      router.push("/jobs");
    } else {
      throw new Error(`Failed to delete job. Status code: ${response.status}`);
    }
  } catch (error) {
    toast.error("Job not deleted");
    console.error("Error deleting job:", error);
  }
};
}

</script>

<template>
  <BackButton />
    <section v-if="!state.isLoading" class="bg-violet-50">
      <div class="container m-auto py-10 px-6">
        <div class="grid grid-cols-1 md:grid-cols-70/30 w-full gap-6">
          <main>
            <div
              class="bg-white p-6 rounded-lg shadow-md text-center md:text-left"
            >
              <div class="text-gray-500 mb-4">{{state.job.type}}</div>
              <h1 class="text-3xl font-bold mb-4">{{state.job.title}}</h1>
              <div
                class="text-gray-500 mb-4 flex align-middle justify-center md:justify-start"
              >
                <i
                  class="pi pi-map-marker text-lg text-orange-700 mr-2"
                ></i>
                <p class="text-orange-700">{{state.job.location}}</p>
              </div>
            </div>

            <div class="bg-white p-6 rounded-lg shadow-md mt-6">
              <h3 class="text-violet-800 text-lg font-bold mb-6">
                Job Description
              </h3>

              <p class="mb-4">
                {{state.job.description}}
              </p>

              <h3 class="text-violet-800 text-lg font-bold mb-2">Salary</h3>

              <p class="mb-4">{{state.job.salary}} / Year</p>
            </div>
          </main>

          <!-- Sidebar -->
          <aside>
            <!-- Company Info -->
            <div class="bg-white p-6 rounded-lg shadow-md">
              <h3 class="text-xl font-bold mb-6">Company Info</h3>

              <h2 class="text-2xl">{{state.job.company.name}}</h2>

              <p class="my-2">
                {{state.job.company.description}}
              </p>

              <hr class="my-4" />

              <h3 class="text-xl">Contact Email:</h3>

              <p class="my-2 bg-violet-100 p-2 font-semibold truncate">
                {{state.job.company.contactEmail}}
              </p>

              <h3 class="text-xl">Contact Phone:</h3>

              <p class="my-2 bg-violet-100 p-2 font-semibold">{{state.job.company.contactPhone}}</p>
            </div>

            <!-- Manage -->
            <div class="bg-white p-6 rounded-lg shadow-md mt-6">
              <h3 class="text-xl font-bold mb-6">Manage Job</h3>
              <RouterLink
                :to="`/jobs/edit/${state.job.id}`"
                class="bg-violet-500 hover:bg-violet-600 text-white text-center font-bold py-2 px-4 rounded-full w-full focus:outline-none focus:shadow-outline mt-4 block"
                >Edit Job</RouterLink
              >
              <button
              @click="deleteJob"
              type= "button"
                class="bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded-full w-full focus:outline-none focus:shadow-outline mt-4 block"
              >
                Delete Job
              </button>
            </div>
          </aside>
        </div>
      </div>
    </section>
    <section v-else class="text-center text-yellow-600 animate-pulse font-semibold text-3xl mt-4">
    
    Loading Jobs...
    </section>
</template>