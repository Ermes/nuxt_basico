<template>
  <v-card title="Login" subtitle="Introduce las credenciales" class="mx-auto px-6 py-6" width="400" elevation="5">
    <v-card-text class="my-2">
      <v-form v-model="form" @submit.prevent="onSubmit">
        <v-text-field v-model="email" :readonly="loading" :rules="[required]" class="mb-1" label="Email" clearable density="compact"></v-text-field>
        <v-text-field v-model="password" :readonly="loading" :rules="[required]" label="Password" clearable density="compact" type="password"></v-text-field>
      </v-form>
    </v-card-text>
    <v-card-actions>
      <v-btn :disabled="!form" :loading="loading" color="primary" size="large" type="submit" variant="elevated" block density="compact"> Sign In </v-btn>
      <div>{{ password }}</div>
    </v-card-actions>
  </v-card>
</template>

<script setup>
import { ref } from 'vue'

const form = ref(false)
const email = ref(null)
const password = ref(null)
const loading = ref(false)

function onSubmit() {
  if (!form.value) return
  loading.value = true
  setTimeout(() => (loading.value = false), 2000)
}
function required(v) {
  return !!v || 'Field is required'
}
</script>
