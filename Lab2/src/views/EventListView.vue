<script setup lang="ts">
  import EventCard from '@/components/EventCard.vue'
  import Categories from '@/components/Categories.vue'
  import type { Event } from '@/types'
  import { ref, onMounted } from 'vue'
  import axios from 'axios'

const events = ref<Event[] | null>(null)

onMounted(async () => {
  try {
    const response = await axios.get<Event[]>('https://my-json-server.typicode.com/dokeshi1090/Mock-Server_lab2/events')
    events.value = response.data
  } catch (error) {
    console.error('There was an Error:', error)
  }
})
</script>



<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <Categories v-for="event in events" :key="'cat-' + event.id" :event="event" />
  </div>
</template>

<style scoped>

.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>
