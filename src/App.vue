<script setup>
import AppAllert from "./components/AppAllert.vue";
import {ref} from "vue"
const alerts = ref([
  {
    type: "info",
    massage: "New software update available."
  },
  {
    type: "success",
    massage: "Your purchase has been confirmed!"
  },
  {
    type: "warning",
    massage: "Warning: Invalid email address!"
  },
  {
    type: "error",
    massage: "Error! Task failed successfully."
  }
])
</script>

<template>
  <AppAllert v-for="alert in alerts" :key="alert.type" :type="alert.type">{{ alert.massage }}</AppAllert>
</template>

<style scoped></style>
