<template>
  <div class="min-h-full">
    <site-navbar />
    <Nuxt />
  </div>
</template>

<script>
import siteNavbar from "@/components/siteNavbar.vue";

export default {
  components: {
    siteNavbar
  }
};
</script>
