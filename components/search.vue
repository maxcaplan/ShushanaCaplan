<template>
  <div class="relative rounded-md">
    <input
      type="text"
      name="price"
      id="price"
      class="block w-full pl-3 pr-9 py-2 rounded-md border border-solid border-gray-300 focus:ring-2"
      placeholder="search..."
      v-model="query"
    />

    <div
      class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none"
    >
      <span class="text-gray-500">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5"
          viewBox="0 0 20 20"
          fill="currentColor"
        >
          <path
            fill-rule="evenodd"
            d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
            clip-rule="evenodd"
          />
        </svg>
      </span>
    </div>

    <div v-show="results" class="absolute mt-2">
      <BaseCard class="bg-white">
        <ul class="w-full">
          <li v-for="result in results" :key="result.slug" class="block w-full">
            <button
              class="bg-white hover:bg-gray-100 py-2 px-4 block w-full whitespace-no-wrap text-left"
              @click="resultClick(route(result.dir, result.slug))"
            >
              {{ result.title }}
            </button>
          </li>
        </ul>
      </BaseCard>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: "",
      results: []
    };
  },

  watch: {
    async query(query) {
      if (!query) {
        this.results = [];
        return;
      }

      this.results = await this.$content("work", { deep: true })
        .sortBy("createdAt", "desc")
        .limit(12)
        .search(query)
        .fetch();
    }
  },

  methods: {
    route(dir, slug) {
      dir = dir.slice(6);
      return `/works/${dir}/${slug}`;
    },

    resultClick(route) {
      this.results = [];
      this.query = "";
      this.$router.push(route);
    }
  }
};
</script>
