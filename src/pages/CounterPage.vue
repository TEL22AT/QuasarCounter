<template>
  <q-page class="flex flex-center">
    <CounterCard @increment-counter="counterIncremented" />
  </q-page>
</template>

<script setup>
import CounterCard from 'src/components/CounterCard.vue'
function counterIncremented(data) {
  console.log('Counter incremented: ', data)
}
</script>
