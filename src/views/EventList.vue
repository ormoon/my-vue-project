<template>
  <h1>Events For Good</h1>
  <div class="home">
    <EventCard v-for="event in events" :key="event.id" :msg="event" />
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
      .then((res) => {
        this.events = res.data
      })
      .catch((err) => {
        console.log('Error >> ', err)
      })
  },
}
</script>
<style scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
