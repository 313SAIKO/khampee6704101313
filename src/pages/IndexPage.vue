<template>
  <q-page class="q-pa-md">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input filled v-model="name" label="Your name" hint="Name and surname" />
      <q-input filled v-model.number="age" label="Your age" type="number" />
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
import { useQuasar } from 'quasar'

const $q = useQuasar()
const name = ref('')
const age = ref(null)
const accept = ref(false)

function onSubmit() {
  if (!accept.value) {
    $q.notify({
      type: 'negative',
      message: 'You need to accept the terms'
    })
  } else {
    $q.notify({
      type: 'positive',
      message: `Submitted successfully! Name: ${name.value}, Age: ${age.value}`
    })
  }
}

function onReset() {
  name.value = ''
  age.value = null
  accept.value = false
}
</script>
