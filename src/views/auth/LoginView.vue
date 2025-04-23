<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row class="d-flex justify-end">
        <v-col cols="12" md="6" class="opacity-80 d-flex justify-center">
          <v-card
            class="mx-auto justify-center bg-grey-darken-3"
            elevation="8"
            subtitle="“Your Spot,  Your Business, Your Advantage!”"
          >
            <template v-slot:title>
              <img
                src="../../../public/images/VendorVantage.png"
                alt=""
                height="200px"
                width="400px"
              />
            </template>

            <v-card-text class="bg-grey-darken-3 pt-4">
              <v-form fast-fail @submit.prevent>
                <v-text-field label="Email"></v-text-field>

                <v-text-field label="Password" type="password"></v-text-field>

                <v-btn class="mt-2" elevation="12" type="submit" block color="grey-darken-1"
                  >Login</v-btn
                >
                <v-divider class="my-5"></v-divider>
                <h5 class="text-center">
                  Don't Have an account?
                  <RouterLink class="text-light-blue-accent-3" to="register"
                    >Click here to register</RouterLink
                  >
                </h5>
              </v-form>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>
