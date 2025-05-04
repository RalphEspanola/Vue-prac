<script setup>
import HeaderView from '@/components/layout/HeaderView.vue'
import EventHolder from '@/components/layout/EventHolder.vue'
import EventCarousel from '@/components/layout/EventCarousel.vue'
</script>

<template>
  <v-layout>
    <HeaderView></HeaderView>
    <v-row class="mt-7">
      <v-col cols="12" md="12" class="mt-16 mb-14">
        <EventCarousel></EventCarousel>
      </v-col>
      <v-col cols="12" md="7" class="pl-10"><EventHolder></EventHolder></v-col>
      <v-col cols="12" md="5" class="d-flex justify-center ml-n10">
        <VCalendar />
      </v-col>
    </v-row>
  </v-layout>
</template>
