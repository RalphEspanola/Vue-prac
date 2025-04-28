<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import RegisterForm from '@/components/auth/RegisterForm.vue'
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row class="d-flex justify-end">
        <v-hover v-slot="{ isHovering, props }">
          <v-col cols="12" md="6" class="opacity-80 d-flex justify-center">
            <v-card
              class="mx-auto justify-center bg-grey-darken-3 px-10"
              subtitle="“Your Spot,  Your Business, Your Advantage!”"
              v-bind="props"
              :elevation="isHovering ? 24 : 6"
            >
              <template v-slot:title>
                <img src="/public/images/VendorVantage.png" alt="" height="200px" width="400px" />
              </template>
              <v-card-text class="bg-grey-darken-3 pt-4">
                <v-divider class="my-5"></v-divider>
              </v-card-text>

              <RegisterForm></RegisterForm>
              <h5 class="text-center pt-8 pb-10">
                Already have an account?
                <RouterLink class="text-light-blue-accent-3" to="/">Click here to login</RouterLink>
              </h5>
            </v-card>
          </v-col>
        </v-hover>
      </v-row>
    </template>
  </AppLayout>
</template>
