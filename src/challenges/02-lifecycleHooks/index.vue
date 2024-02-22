<template>
  <div>
    <Child v-if="visible" />

    <div>
      <button @click="handleToggle">
        Toggle Child Component
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { provide, ref } from 'vue'
import Child from './Child.vue'

const visible = ref(true)
const count = ref(0)
const timer = ref(null)

provide('timer', timer)
provide('count', count)

function handleToggle() {
  visible.value = !visible.value
}
</script>

<style scoped></style>