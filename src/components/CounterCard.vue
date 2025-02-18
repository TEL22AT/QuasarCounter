<template>
  <q-card class="my-card bg-secondary text-white">
    <q-card-section v-if="props.heading">
      <div class="text-h6">Counter State</div>
    </q-card-section>

    <q-card-section>
      <div :style="isCounterEven ? 'color: green' : 'color: red'">
        {{ counterStore.counter }}
        <q-icon v-if="counterStore.counter % 2 == 0" :name="mdiCheck"></q-icon>
        <q-icon v-else :name="mdiClose"></q-icon>
      </div>
    </q-card-section>

    <q-separator dark />

    <q-card-actions>
      <q-btn flat @click="incrementCounter()">Increase</q-btn>
      <q-btn flat @click="counterStore.reset()">Reset</q-btn>
    </q-card-actions>
  </q-card>
</template>

<script setup>
import { mdiCheck, mdiClose } from '@quasar/extras/mdi-v4'
import { useCounterStore } from 'src/stores/counter'
import { computed } from 'vue'

const props = defineProps({
  heading: {
    type: Boolean,
    default: false,
  },
})

const emit = defineEmits(['incrementCounter'])

function incrementCounter() {
  counterStore.increment()
  emit('incrementCounter', counterStore.counter)
}

const counterStore = useCounterStore()
const isCounterEven = computed(() => counterStore.counter % 2 === 0)
</script>
