<template>
  <div class="events">
    <h1>Events For Good</h1>
    <router-link to="/event/123">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
    </router-link>
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService'

export default {
  name: 'EventList',
  components: {
    EventCard,
  },
  data() {
    return {
      events: null,
    }
  },

  created() {
    EventService.getEvents()
      .then((response) => {
        this.events = response.data
      })
      .catch((error) => console.log(error))
  },
}
</script>
<style lang="scss" scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
