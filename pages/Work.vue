<template>
  <div id="work" class="container mx-auto p-3 sm:px-0 space-y-5">
    <div>
      <p class="inline text-3xl font-bold border-b-2 border-gray-300">
        Collections
      </p>
    </div>

    <div class="grid grid-cols-3 gap-4 mb-5">
      <div v-for="collection in collections" :key="collection.slug">
        <CollectionCard :collection="collection" />
      </div>
    </div>

    <div>
      <p class="inline text-3xl font-bold border-b-2 border-gray-300">
        Recent Work
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
  async asyncData({ $content }) {
    const works = await $content("work", { deep: true })
      .sortBy("createdAt", "desc")
      .limit(6)
      .fetch();

    const collections = await $content("categories", { deep: true })
      .sortBy("title")
      .fetch();

    return {
      works,
      collections
    };
  }
};
</script>
