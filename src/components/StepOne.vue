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
        @input="$emit('sendName', $event.target.value)"
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
          class="inline-flex mb-2 text-sm text-gray-800 mt-5"
      >
        Ostavite vase misljenje:
      </label>
      <textarea
        @input="$emit('sendDesc', $event.target.value)"
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

import {ref, computed} from 'vue'

const emit = defineEmits([
  'sendName',
  'sendDesc'
])

</script>

