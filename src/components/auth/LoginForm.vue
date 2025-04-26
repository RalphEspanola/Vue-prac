<script setup>
import { ref } from 'vue'

const visible = ref(false) // This controls password visibility toggle
</script>

<template>
  <v-form fast-fail @submit.prevent>
    <v-text-field
      placeholder="Email address"
      prepend-inner-icon="mdi-email-outline"
      variant="outlined"
    ></v-text-field>
    <v-text-field
      :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
      :type="visible ? 'text' : 'password'"
      placeholder="Enter your password"
      prepend-inner-icon="mdi-lock-outline"
      variant="outlined"
      @click:append-inner="visible = !visible"
    ></v-text-field>
    <v-btn
      class="mt-2"
      elevation="12"
      type="submit"
      block
      color="grey-darken-1"
      prepend-icon="mdi-login"
      >Login</v-btn
    >
    <v-divider class="my-5"></v-divider>
  </v-form>
</template>
