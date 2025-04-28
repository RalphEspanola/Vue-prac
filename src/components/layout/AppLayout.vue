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
          no-repeat
          center
          cover
        >
          <v-row justify="end">
            <v-col cols="auto" class="mr-4 mt-5">
              <v-btn
                :icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
                slim
                @click="onClick"
                variant="elevated"
                :color="theme === 'light' ? 'yellow-lighten-3' : 'yellow-darken-2'"
              ></v-btn>
            </v-col>
          </v-row>

          <v-container>
            <slot name="content"></slot>
          </v-container>
        </v-img>
      </v-main>
    </v-app>
  </v-responsive>
</template>

<style scoped></style>
