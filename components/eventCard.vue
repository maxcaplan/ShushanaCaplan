<template>
  <BaseCard>
    <BaseCardBody>
      <Nuxt-link :to="'/events/' + event.slug" class="flex flex-row space-x-5">
        <!-- Event image -->
        <div class="w-48 h-24 rounded overflow-hidden">
          <div
            v-show="!event.image"
            class="w-full h-full bg-gray-300 flex justify-center items-center"
          >
            <p class="text-gray-600 text-4xl font-bold">
              {{ initial }}
            </p>
          </div>

          <div
            v-show="event.image"
            class="w-full h-full bg-cover bg-center bg-no-repeat"
            :style="{ backgroundImage: backgroundImage }"
          ></div>
        </div>

        <div class="flex flex-col space-y-1">
          <p class="text-gray-900 text-xl font-bold">
            {{ event.title }}
          </p>

          <p class="text-gray-900 text-xl">
            {{ event.start }}
          </p>

          <p class="text-gray-600">
            {{ event.description }}
          </p>
        </div>
      </Nuxt-link>
    </BaseCardBody>
  </BaseCard>
</template>

<script>
export default {
  props: {
    event: {
      type: Object,
      required: true
    }
  },

  computed: {
    initial() {
      if (this.event && this.event.title) {
        return this.event.title.charAt(0);
      } else {
        return "E";
      }
    },
    backgroundImage() {
      if (this.event.image) {
        return 'url("' + this.event.image + '")';
      } else {
        return "";
      }
    }
  }
};
</script>
