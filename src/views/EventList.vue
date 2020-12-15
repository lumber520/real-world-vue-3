<template>
  <div class="events">
    <EventCrad v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCrad from "@/components/EventCard.vue";
import EventService from "../services/EventService.js";

export default {
  name: "EventList",
  components: {
    EventCrad
  },
  data() {
    return {
      events: null
    };
  },
  created() {
    EventService.getEvents()
      .then(response => {
        this.events = response.data;
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
