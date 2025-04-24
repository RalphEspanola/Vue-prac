<script setup>
import { ref } from 'vue'
import AppLayout from '@/components/layout/AppLayout.vue'

const isPasswordVisible = ref(false)
const isPasswordConfirmVisible = ref(false)
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row class="d-flex justify-end">
        <v-hover v-slot="{ isHovering, props }">
          <v-col cols="12" md="6" class="opacity-80 d-flex justify-center">
            <v-card
              class="mx-auto justify-center bg-grey-darken-3"
              subtitle="“Your Spot,  Your Business, Your Advantage!”"
              v-bind="props"
              :elevation="isHovering ? 24 : 6"
            >
              <template v-slot:title>
                <img src="/public/images/VendorVantage.png" alt="" height="200px" width="400px" />
              </template>
              <v-card-text class="bg-grey-darken-3 pt-4">
                <v-form fast-fail @submit.prevent
                  ><v-divider class="my-3"></v-divider>
                  <v-row>
                    <v-col cols="12" md="6">
                      <v-text-field label="First Name" variant="outlined"></v-text-field>
                    </v-col>
                    <v-col cols="12" md="6">
                      <v-text-field label="Last Name" variant="outlined"></v-text-field>
                    </v-col>
                    <v-col cols="12">
                      <v-text-field
                        prepend-inner-icon="mdi-email-outline"
                        label="Email"
                        variant="outlined"
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" md="6">
                      <v-text-field
                        :append-inner-icon="isPasswordVisible ? 'mdi-eye' : 'mdi-eye-off'"
                        prepend-inner-icon="mdi-lock-outline"
                        :type="isPasswordVisible ? 'text' : 'password'"
                        label="Password"
                        variant="outlined"
                        @click:append-inner="isPasswordVisible = !isPasswordVisible"
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" md="6">
                      <v-text-field
                        :append-inner-icon="isPasswordConfirmVisible ? 'mdi-eye' : 'mdi-eye-off'"
                        prepend-inner-icon="mdi-lock-outline"
                        :type="isPasswordConfirmVisible ? 'text' : 'password'"
                        label="Password"
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
                      prepend-icon="mdi-account-plus"
                      >Register</v-btn
                    ></v-row
                  >
                  <v-divider class="my-5"></v-divider>
                  <h5 class="text-center my-2">
                    Already have an account?
                    <RouterLink class="text-light-blue-accent-3" to="/"
                      >Click here to login</RouterLink
                    >
                  </h5>
                </v-form>
              </v-card-text>
            </v-card>
          </v-col>
        </v-hover>
      </v-row>
    </template>
  </AppLayout>
</template>
