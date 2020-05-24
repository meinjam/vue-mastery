<template>
  <div>
    <h1>Event Listing</h1>
    <EventCard v-for="event in events" :key="event.id" v-bind:event="event" />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard.vue";
import EventService from "@/services/EventService.js";

export default {
  components: {
    EventCard,
  },
  data() {
    return {
      events: [],
    };
  },
  created() {
    EventService.getEvents()
      .then((resp) => (this.events = resp.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style scoped></style>
