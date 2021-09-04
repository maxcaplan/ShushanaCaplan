<template>
  <nav class="bg-white border-b">
    <div class="container mx-auto px-3 sm:px-0">
      <div class="flex justify-between items-center h-16">
        <nuxt-link to="/" class="text-lg sm:text-2xl font-bold"
          >Shushana Caplan</nuxt-link
        >

        <!-- Desktop Navigation -->
        <div class="hidden lg:flex space-x-4 items-center">
          <div class="flex space-x-4">
            <div class="group inline-block relative">
              <Nuxt-link
                to="/work"
                class="px-3 py-2 rounded-md group-hover:bg-gray-100 focus:ring-2 flex items-center space-x-1"
              >
                <p>Work</p>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-5 w-5"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                >
                  <path
                    fill-rule="evenodd"
                    d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                    clip-rule="evenodd"
                  />
                </svg>
              </Nuxt-link>

              <ul
                class="absolute hidden text-gray-900 pt-1 group-hover:inline-block w-56"
              >
                <div class="rounded border border-gray-200">
                  <li v-for="collection in collections" :key="collection.slug">
                    <Nuxt-link
                      class="bg-white hover:bg-gray-100 py-2 px-4 block whitespace-no-wrap"
                      :to="'/works/' + collection.slug"
                    >
                      {{ collection.title }}
                    </Nuxt-link>
                  </li>
                </div>
              </ul>
            </div>

            <Nuxt-link
              to="/about"
              class="px-3 py-2 rounded-md hover:bg-gray-100 focus:ring-2"
              >About
            </Nuxt-link>

            <Nuxt-link
              to="/events"
              class="px-3 py-2 rounded-md hover:bg-gray-100 focus:ring-2"
              >Events
            </Nuxt-link>
          </div>

          <div class="relative rounded-md">
            <input
              type="text"
              name="price"
              id="price"
              class="block w-full pl-3 pr-9 py-2 rounded-md border border-solid border-gray-300 focus:ring-2"
              placeholder="search..."
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
          </div>
        </div>

        <!-- Mobile Menu Toggle -->
        <button
          @click="mobileMenuOpen = !mobileMenuOpen"
          class="flex lg:hidden p-2 rounded-md hover:bg-gray-100"
        >
          <!-- Menu Icon -->
          <svg
            v-show="!mobileMenuOpen"
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
          </svg>

          <!-- Close Icon -->
          <svg
            v-show="mobileMenuOpen"
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>

      <!-- Mobile Navigation -->
      <div
        class="w-full flex-col pb-3 space-y-3"
        :class="mobileMenuOpen ? 'flex' : 'hidden'"
      >
        <div class="w-full flex flex-col space-y-1">
          <Nuxt-link
            to="/work"
            href="#"
            class="px-3 py-2 rounded-md text-center hover:bg-gray-100 focus:ring-2"
          >
            Work
          </Nuxt-link>

          <Nuxt-link
            to="/about"
            href="#"
            class="px-3 py-2 rounded-md text-center hover:bg-gray-100 focus:ring-2"
          >
            About
          </Nuxt-link>

          <a
            href="#"
            class="px-3 py-2 rounded-md text-center hover:bg-gray-100 focus:ring-2"
            >Events</a
          >

          <a
            href="#"
            class="px-3 py-2 rounded-md text-center hover:bg-gray-100 focus:ring-2"
            >Blog</a
          >
        </div>

        <div class="relative rounded-md">
          <input
            type="text"
            name="price"
            id="price"
            class="block w-full pl-3 pr-9 py-2 rounded-md border border-solid border-gray-300 focus:ring-2"
            placeholder="search..."
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
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      mobileMenuOpen: false,
      collections: []
    };
  },

  async fetch() {
    this.collections = await this.$content("categories", { deep: true })
      .sortBy("title")
      .fetch();
  },

  mounted() {
    this.handleResize();
    window.addEventListener("resize", this.handleResize);
  },

  beforeDestroy() {
    window.removeEventListener("resize", this.handleResize);
  },

  methods: {
    handleResize() {
      // Close mobile menu if page resized to desktop size
      this.mobileMenuOpen = window.innerWidth < 1024 && this.mobileMenuOpen;
    }
  }
};
</script>

<style></style>
