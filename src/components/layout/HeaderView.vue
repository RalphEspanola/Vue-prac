<script setup>
import ProfileHeader from './ProfileHeader.vue'
import { isAuthenticated } from '@/utils/supabase'
import { onMounted, ref, watch } from 'vue'

const items = [
  {
    title: 'Foo',
    value: 'foo',
  },
  {
    title: 'Bar',
    value: 'bar',
  },
  {
    title: 'Fizz',
    value: 'fizz',
  },
  {
    title: 'Buzz',
    value: 'buzz',
  },
]

const drawer = ref(false)
const group = ref(null)

watch(group, () => {
  drawer.value = false
})

// Load Variables
const isLoggedIn = ref(false)

// Get Authentication status from the supabase
const getLoggedStatus = async () => {
  isLoggedIn.value = await isAuthenticated()
}

// Load Functions during component rendering
onMounted(() => {
  getLoggedStatus()
})
</script>

<template>
  <v-app-bar>
    <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

    <img src="../../../public/images/VendorVantage.png" height="70px" />
    <v-spacer></v-spacer>
    <ProfileHeader v-if="isLoggedIn" justify="end"></ProfileHeader>
  </v-app-bar>

  <v-navigation-drawer
    v-model="drawer"
    :location="$vuetify.display.mobile ? 'bottom' : undefined"
    temporary
  >
    <v-list :items="items"></v-list>
  </v-navigation-drawer>
</template>
