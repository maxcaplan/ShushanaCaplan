<template>
  <div id="events" class="container mx-auto p-3 sm:px-0 space-y-5">
    <div>
      <p class="inline text-3xl font-bold border-b-2 border-gray-300">
        Events
      </p>
    </div>

    <div class="flex flex-col space-y-3">
      <EventCard v-for="event in events" :key="event.slug" :event="event" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const events = await $content("events")
      .sortBy("start", "asc")
      .limit(10)
      .fetch();

    return {
      events
    };
  }
};
</script>
