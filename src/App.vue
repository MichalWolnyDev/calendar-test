<script setup>
import FullCalendar from '@fullcalendar/vue3'
import dayGridPlugin from '@fullcalendar/daygrid'
import timeGridPlugin from '@fullcalendar/timegrid'
import interactionPlugin from '@fullcalendar/interaction'
import { ref } from 'vue'

const handleDateClick = (arg) => {
  alert('date click! ' + arg.dateStr)
}

const toggleWeekends = () => {
  calendarOptions.value.weekends = !calendarOptions.value.weekends
}

const calendarOptions = ref({
  plugins: [dayGridPlugin, interactionPlugin, timeGridPlugin],
  initialView: 'dayGridMonth',
  headerToolbar: {
    left: 'prev,next',
    center: 'title',
    right: 'timeGridWeek,timeGridDay' // user can switch between the two
  },
  dateClick: handleDateClick,
  nextDayThreshold: '09:00:00',
  events: [
    {
      // Goes from 8pm to 10am the next day.
      title: 'Event 2',
      start: '2023-09-04T20:00:00',
      end: '2023-09-05T10:00:00'
    }
  ],
  weekends: false,
  selectable: true
})


</script>

<template>
  <button @click="toggleWeekends">toggle weekends</button>
  <FullCalendar :options="calendarOptions" />
</template>

<style scoped></style>
