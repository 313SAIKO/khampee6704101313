<template>
  <q-page class="flex flex-center">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        filled
        v-model="name"
        label="Your name"
        :rules="[val => !!val || 'Please type something']"
      />

      <q-input
        filled
        v-model="age"
        label="Your age"
        type="number"
        :rules="[
          val => !!val || 'Please type your age',
          val => val > 0 || 'Please type a real age'
        ]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary" />
        <q-btn label="Reset" type="reset" color="secondary" flat />
      </div>
    </q-form>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const name = ref('')
const age = ref(null)
const accept = ref(false)

function onSubmit () {
  if (accept.value) {
    alert('Submitted!')
  }
}

function onReset () {
  name.value = ''
  age.value = null
  accept.value = false
}
</script>
