<template>
  <BaseCard>
    <div class="image" :style="backgroundImage(collection.image)"></div>

    <BaseCardBody>
      <div class="flex flex-row mb-1">
        <p class="text-xl flex flex-grow">{{ collection.title }}</p>

        <nuxt-link
          to="/works/abstract_landscapes"
          class="rounded p-2 bg-white hover:bg-gray-100"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
              clip-rule="evenodd"
            />
          </svg>
        </nuxt-link>
      </div>

      <p class="text-gray-500">{{ collection.description }}</p>
    </BaseCardBody>
  </BaseCard>
</template>

<script>
export default {
  props: {
    collection: {
      type: Object,
      required: true
    }
  },

  methods: {
    backgroundImage(img) {
      return 'background-image: url("' + img + '")';
    }
  }
};
</script>

<style scoped>
.image {
  @apply w-full h-64 bg-center bg-cover bg-no-repeat;
}
</style>
