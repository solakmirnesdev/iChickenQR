<template>
  <div>
    <div class="flex flex-col mb-4 mt-5">
      <label
        for="name"
        class="inline-flex mb-2 text-sm text-gray-800"
      >
        Unesite vase ime (Opcionalno):
      </label>
      <input
        name="name"
        v-model="name"
        class="
          w-full
          px-3
          py-2
          text-gray-800
          border
          rounded
          outline-none
          bg-gray-50
          focus:ring
          ring-indigo-300
        "
      />
      <label
          for="name"
          class="inline-flex mb-2 text-sm text-gray-800 mt-5"
      >
        Ostavite vase misljenje:
      </label>
      <textarea
        v-model="desc"
        rows="4"
        class="
          w-full
          text-gray-800
          border
          rounded
          outline-none
          bg-gray-50
          focus:ring
          ring-indigo-300"
      ></textarea>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const emit = defineEmits([
    'sendCred'
])

const name = ref('')
const desc = ref('')

const sendData = computed(() => {
  return `${name.value} ${desc.value}`
})

const sendCred = () => {
  emit('sendCred', sendData)
}
</script>

