<script setup>
import MiniCalendar from '@/components/layout/MiniCalendar.vue'
import { isAuthenticated } from '@/utils/supabase'
import { onMounted, ref } from 'vue'

import { useDisplay } from 'vuetify'

// Load Variables
const isLoggedIn = ref(false)

// Get Authentication status from the supabase
const getLoggedStatus = async () => {
  isLoggedIn.value = await isAuthenticated()
}

// User information
const user = {
  initials: 'JD',
  fullName: 'John Doe',
  email: 'john.doe@doe.com',
}

// Carousel setup
const colors = ['indigo', 'warning', 'pink-darken-2', 'red-lighten-1', 'deep-purple-accent-4']
const slides = ['First', 'Second', 'Third', 'Fourth', 'Fifth']

// Load Functions during component rendering
onMounted(() => {
  getLoggedStatus()
})
</script>

<template>
  <v-layout>
    <v-app-bar :elevation="2">
      <template v-slot:prepend>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
      </template>
      <v-app-bar-title>
        <img src="../../../public/images/VendorVantage.png" height="60" alt="VendorVantage Logo" />
      </v-app-bar-title>
      <v-spacer></v-spacer>
      <v-menu min-width="200" location="bottom end">
        <template v-slot:activator="{ props }">
          <v-btn icon v-bind="props">
            <v-avatar color="brown" size="large">
              <span class="text-h5">{{ user.initials }}</span>
            </v-avatar>
          </v-btn>
        </template>
        <v-card>
          <v-card-text>
            <div class="mx-auto text-center">
              <v-avatar color="brown">
                <span class="text-h5">{{ user.initials }}</span>
              </v-avatar>
              <h3>{{ user.fullName }}</h3>
              <p class="text-caption mt-1">
                {{ user.email }}
              </p>
              <v-divider class="my-3"></v-divider>
              <v-btn variant="text" rounded> Edit Account </v-btn>
              <v-divider class="my-3"></v-divider>
              <v-btn variant="text" rounded> Disconnect </v-btn>
            </div>
          </v-card-text>
        </v-card>
      </v-menu>
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <v-row>
          <v-col cols="12" md="12">
            <v-carousel height="400" :show-arrows="true" cycle hide-delimiter-background>
              <v-carousel-item v-for="(slide, i) in slides" :key="i">
                <v-sheet :color="colors[i]" height="100%">
                  <div class="d-flex fill-height justify-center align-center">
                    <div class="text-h2">{{ slide }} Slide</div>
                  </div>
                </v-sheet>
              </v-carousel-item>
            </v-carousel>
          </v-col>

          <v-col cols="12" md="4">
            <MiniCalendar></MiniCalendar>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-layout>
</template>
