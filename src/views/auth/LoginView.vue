<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import LoginForm from '@/components/auth/LoginForm.vue'
</script>

<template>
  <AppLayout>
    <template #content>
      <v-container fluid>
        <v-row class="d-flex justify-end">
          <v-hover v-slot="{ isHovering, props }">
            <v-col cols="12" md="6" class="opacity-80 d-flex justify-center">
              <v-card
                class="mx-auto justify-center bg-grey-darken-3 px-10"
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
                <v-card-text class="bg-grey-darken-3 pt-4"> </v-card-text>

                <LoginForm></LoginForm>
                <h5 class="text-center pb-6">
                  Don't Have an account?
                  <RouterLink class="text-light-blue-accent-3" to="register"
                    >Click here to register</RouterLink
                  >
                </h5>
              </v-card>
            </v-col>
          </v-hover>
        </v-row>
      </v-container>
    </template>
  </AppLayout>
</template>
