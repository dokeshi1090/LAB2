<script setup lang="ts">
  import StudentCard from '@/components/StudentCard.vue'
  import Categories from '@/components/Categories.vue'
  import type { Event, Student } from '@/types'
  import { ref, onMounted } from 'vue'
  import EventService from '@/services/EventService'
  import StudentService from '@/services/StudentService'

const events = ref<Event[] | null>(null)
const students = ref<Student[] | null>(null)

onMounted(() => {
   EventService.getEvents()
    .then ((response) => {
      events.value = response.data
    })
})

onMounted(() => {
   StudentService.getStudents()
    .then((response) => {
      students.value = response.data
    })
})

</script>



<template>
    <h1>Students</h1>
  <div class="students">
    <div v-for="student in students" :key="student.id" class="student-card">
      <p><b>{{ student.name }} {{ student.surname }}</b></p>
      <p>GPA: {{ student.gpa }}</p>
    </div>
  </div>
</template>

<style scoped>

.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.students {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}

.student-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
}

.student-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}

</style>