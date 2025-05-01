<script setup>
import { ref } from 'vue'

const theme = ref(localStorage.getItem('theme') ?? 'light')

function onClick() {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
  localStorage.setItem('theme', theme.value)
}
</script>

<template>
  <v-responsive>
    <v-app :theme="theme">
      <v-main>
        <v-img
          :src="theme === 'light' ? '/images/BodyLight.png' : '/images/BodyDark.png'"
          height="100%"
          no-repeat
          center
          cover
        >
          <v-container>
            <v-col cols="12" class="d-flex justify-end mt-5">
              <v-btn
                :icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
                slim
                @click="onClick"
                variant="elevated"
                :color="theme === 'light' ? 'yellow-lighten-3' : 'yellow-darken-2'"
              ></v-btn>
            </v-col>
            <slot name="content"></slot>
          </v-container>
        </v-img>
      </v-main>
    </v-app>
  </v-responsive>
</template>

<style scoped></style>
