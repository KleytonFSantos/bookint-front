<script setup lang="ts">
    const { pending, data: bookings } = await useFetch('http://localhost:8000/booking-list')
</script>
<template>
 <!-- you will need to handle a loading state -->
 <div v-if="pending">
    Loading ...
  </div>
  <div v-else>
    <div v-for="booking in bookings">
       <div> {{ booking.user.name }}</div>
    </div>
  </div>
</template>