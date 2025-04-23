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
      <v-main>
        <v-img
          :src="theme === 'light' ? '/images/BodyLight.png' : '/images/BodyDark.png'"
          no-repeat
          center
          cover
          ><v-row justify="end" class="pt-5 pr-11">
            <v-btn
              :icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
              slim
              @click="onClick"
              variant="elevated"
              :color="theme === 'light' ? 'yellow-lighten-3' : 'yellow-darken-2'"
            ></v-btn>
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
