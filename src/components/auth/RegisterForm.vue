<script setup>
import {
  requiredValidator,
  emailValidator,
  passwordValidator,
  confirmedValidator,
} from '@/utils/validators'
import { ref } from 'vue'

const formDataDefault = {
  firstname: '',
  lastname: '',
  email: '',
  password: '',
  password_confirmation: '',
}

const formData = ref({
  ...formDataDefault,
})

const isPasswordVisible = ref(false)
const isPasswordConfirmVisible = ref(false)
const refVForm = ref()

// Functions
const onSubmit = () => {
  // alert(formData.value.email)
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({ valid }) => {
    if (valid) onSubmit()
  })
}
</script>

<template>
  <v-form ref="refVForm" @submit.prevent="onFormSubmit">
    <v-row>
      <v-col col="12" md="6">
        <v-text-field
          v-model="formData.firstname"
          label="Firstname"
          variant="outlined"
          :rules="[requiredValidator]"
        ></v-text-field>
      </v-col>
      <v-col col="12" md="6">
        <v-text-field
          v-model="formData.lastname"
          label="Last Name"
          variant="outlined"
          :rules="[requiredValidator]"
        ></v-text-field>
      </v-col>
      <v-col col="12" md="12">
        <v-text-field
          v-model="formData.email"
          label="Email address"
          prepend-inner-icon="mdi-email-outline"
          variant="outlined"
          :rules="[requiredValidator, emailValidator]"
        ></v-text-field>
      </v-col>
      <v-col col="12" md="6">
        <v-text-field
          v-model="formData.password"
          :append-inner-icon="isPasswordVisible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="isPasswordVisible ? 'text' : 'password'"
          label="Password"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="isPasswordVisible = !isPasswordVisible"
          :rules="[requiredValidator, passwordValidator]"
        ></v-text-field>
      </v-col>
      <v-col col="12" md="6">
        <v-text-field
          v-model="formData.password_confirmation"
          :append-inner-icon="isPasswordConfirmVisible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="isPasswordConfirmVisible ? 'text' : 'password'"
          label="Password Confirmation"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="isPasswordConfirmVisible = !isPasswordConfirmVisible"
          :rules="[
            requiredValidator,
            confirmedValidator(formData.password_confirmation, formData.password),
          ]"
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
