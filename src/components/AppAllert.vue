<script setup>
import { reactive, ref } from "vue";
const props = defineProps({
  type: { type: String, Required: true },
});
const input = ref("");
input.value = props.type;
const icons = reactive({
  info: "M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z",
  success: "M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z",
  warning:
    "M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z",
  error: "M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z",
});
const closed = ref(false);
function close() {
  closed.value = true;
}
</script>

<template>
  <div v-if="!closed" role="alert" class="alert mb-4" :class="`alert-${input}`">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      class="h-6 w-6 shrink-0 stroke-current"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        stroke-width="2"
        :d="icons[input]"
      ></path>
    </svg>
    <span><slot></slot></span>
    <button @click="close" class="btn" :class="`btn-${input}`">X</button>
  </div>
</template>

<style scoped></style>
