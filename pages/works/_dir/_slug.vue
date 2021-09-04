<template>
  <div id="work" class="container mx-auto p-3 pt-5 sm:px-0 space-y-5">
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

    <div class="grid grid-cols-2 gap-24">
      <img :src="work.image" :alt="work.slug" />

      <div class="flex flex-col space-y-6">
        <h1 class="text-4xl font-bold">{{ work.title }}</h1>

        <p class="text-gray-600">{{ work.medium }} {{ work.dimensions }}</p>

        <p v-show="work.description">{{ work.description }}</p>

        <p class="text-2xl font-bold">${{ work.price }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let work;
    try {
      work = await $content(`work/${params.dir}/${params.slug}`).fetch();
    } catch (e) {
      error({ message: `Work "work/${params.dir}/${params.slug}" not found` });
    }

    return {
      work
    };
  }
};
</script>
