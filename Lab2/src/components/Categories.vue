<script setup lang="ts">
import type { Event } from '@/types'
defineProps<{
  event: Event
}>()
</script>


<template>
  <div class="category-class">
    <div class="category-card">
      <p>{{ event.category }}</p>
      <p>{{ event.organizer }}</p>
    </div>
  </div>
</template>

<style scoped>
.category-card {
  text-align: right;
}
.category-card p {
  font-size: 18px;
  margin: 0;
}
</style>