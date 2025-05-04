<script setup>
import { ref } from 'vue'

const tab = ref(null)
</script>
<template>
  <v-card height="300px">
    <v-tabs v-model="tab" bg-color="grey-darken-1" grow centered>
      <v-tab value="OngoingEvent">
        Ongoing Event
        <v-icon end icon="mdi-calendar-check"></v-icon>
      </v-tab>
      <v-tab value="UpcomingEvent">
        Upcoming Event
        <v-icon end icon="mdi-calendar-clock"></v-icon>
      </v-tab>
    </v-tabs>

    <v-card-text>
      <v-tabs-window v-model="tab">
        <v-tabs-window-item value="OngoingEvent"> One </v-tabs-window-item>
        <v-tabs-window-item value="UpcomingEvent"> Two </v-tabs-window-item>
      </v-tabs-window>
    </v-card-text>
  </v-card>
</template>
