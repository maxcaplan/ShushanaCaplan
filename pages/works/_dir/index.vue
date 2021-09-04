<template>
  <div id="work" class="container mx-auto p-3 sm:px-0 space-y-5">
    <div class="flex flex-row space-x-3">
      <p class="inline text-3xl font-bold border-b-2 border-gray-300">
        Abstract Landscape
      </p>

      <div class="flex flex-grow justify-end">
        <button
          @click="$router.go(-1)"
          class="flex flex-row space-x-3 items-center py-3 px-5 rounded hover:bg-gray-100"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M9.707 16.707a1 1 0 01-1.414 0l-6-6a1 1 0 010-1.414l6-6a1 1 0 011.414 1.414L5.414 9H17a1 1 0 110 2H5.414l4.293 4.293a1 1 0 010 1.414z"
              clip-rule="evenodd"
            />
          </svg>

          <p>Back</p>
        </button>
      </div>
    </div>

    <div class="grid grid-cols-3 gap-4">
      <div v-for="work in works" :key="work.slug">
        <WorkCard :work="work" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    console.log(params.dir);

    const works = await $content("work/" + params.dir)
      .sortBy("createdAt", "desc")
      .fetch();

    return {
      works
    };
  }
};
</script>
