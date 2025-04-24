<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import { ref } from 'vue'

const visible = ref(false)
</script>

<template>
  <AppLayout>
    <template #content>
      <v-container fluid>
        <v-row class="d-flex justify-end">
          <v-hover v-slot="{ isHovering, props }">
            <v-col
              cols="12"
              md="6"
              :class="mobile ? '' : 'pt-16'"
              class="opacity-80 d-flex justify-center"
            >
              <v-card
                class="mx-auto justify-center bg-grey-darken-3"
                v-bind="props"
                :elevation="isHovering ? 24 : 6"
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
          </v-hover>
        </v-row>
      </v-container>
    </template>
  </AppLayout>
</template>
