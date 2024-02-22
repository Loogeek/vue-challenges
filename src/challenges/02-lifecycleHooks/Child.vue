<template>
  <div>
    Child Component: {{ count }}
  </div>
</template>

<script setup lang="ts">
import { onMounted, onBeforeUnmount, inject, Ref } from 'vue'

const timer = inject<Ref>("timer")
const count = inject<Ref>("count")

onMounted(() => {
  timer!.value = window.setInterval(() => {
    count!.value++
  }, 1000)
})

onBeforeUnmount(() => {
  if (timer) {
    timer.value && clearInterval(timer.value)
  }
})

</script>

<style scoped></style>