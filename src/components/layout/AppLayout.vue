<script setup>
import { ref } from 'vue'

const theme = ref('light')

function onClick() {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
}
</script>

<template>
  <v-responsive class="border rounded">
    <v-app :theme="theme">
      <v-app-bar class="px-3" :color="theme === 'light' ? 'yellow-lighten-2' : 'yellow-darken-3'">
        <v-spacer></v-spacer>

        <v-btn
          :icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          slim
          @click="onClick"
          variant="elevated"
          :color="theme === 'light' ? 'yellow-lighten-3' : 'yellow-darken-2'"
        ></v-btn>
      </v-app-bar>

      <v-main>
        <v-img
          :src="theme === 'light' ? '/images/BodyLight.png' : '/images/BodyDark.png'"
          no-repeat
          center
          cover
          class="bg-image"
        >
          <v-container>
            <slot name="content"></slot>
          </v-container>
        </v-img>
      </v-main>

      <v-footer border app :color="theme === 'light' ? 'yellow-lighten-2' : 'yellow-darken-3'"
        >2024 - Praise God</v-footer
      >
    </v-app>
  </v-responsive>
</template>

<style scoped>
.bg-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh; /* Fills the viewport height */
  z-index: 2; /* Ensures the content is above the image */
}
</style>
