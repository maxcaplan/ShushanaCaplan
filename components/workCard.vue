<template>
  <div class="rounded overflow-hidden relative">
    <img :src="work.image" :alt="work.alt" />

    <nuxt-link
      :to="route"
      class="absolute top-0 left-0 w-full h-full opacity-0 hover:opacity-100 transition-opacity duration-300"
    >
      <div class="w-full h-full opacity-50 bg-gray-900"></div>

      <div
        class="absolute top-0 left-0 w-full h-full flex justify-center items-center"
      >
        <p class="text-2xl text-white">{{ work.title }}</p>
      </div>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    work: {
      type: Object,
      required: true
    }
  },

  computed: {
    route() {
      let dir = this.work.dir;
      dir = dir.slice(6);
      return `/works/${dir}/${this.work.slug}`;
    }
  }
};
</script>
