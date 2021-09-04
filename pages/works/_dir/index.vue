<template>
  <div id="work" class="container mx-auto p-3 sm:px-0 space-y-5">
    <div>
      <p class="inline text-3xl font-bold border-b-2 border-gray-300">
        Abstract Landscape
      </p>
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
