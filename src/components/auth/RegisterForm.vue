<script setup>
import { ref } from 'vue'

const isPasswordVisible = ref(false)
const isPasswordConfirmVisible = ref(false)
</script>

<template>
  <v-form fast-fail @submit.prevent>
    <v-row>
      <v-col col="12" md="6">
        <v-text-field placeholder="First Name" variant="outlined"></v-text-field>
      </v-col>
      <v-col col="12" md="6">
        <v-text-field placeholder="Last Name" variant="outlined"></v-text-field>
      </v-col>
      <v-col col="12" md="12">
        <v-text-field
          placeholder="Email address"
          prepend-inner-icon="mdi-email-outline"
          variant="outlined"
        ></v-text-field>
      </v-col>
      <v-col col="12" md="6">
        <v-text-field
          :append-inner-icon="isPasswordVisible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="isPasswordVisible ? 'text' : 'password'"
          placeholder="Enter Password"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="isPasswordVisible = !isPasswordVisible"
        ></v-text-field>
      </v-col>
      <v-col col="12" md="6">
        <v-text-field
          :append-inner-icon="isPasswordConfirmVisible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="isPasswordConfirmVisible ? 'text' : 'password'"
          placeholder="Confirm Password"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="isPasswordConfirmVisible = !isPasswordConfirmVisible"
        ></v-text-field>
      </v-col>
      <v-btn
        class="mt-2"
        elevation="12"
        type="submit"
        block
        color="grey-darken-1"
        prepend-icon="mdi-login"
        >Login</v-btn
      >
    </v-row>
  </v-form>
</template>
