<template>
  <div id="action-buttons">
    <div class="flex mt-5 justify-between">
      <button
        @click="prevStep"
        v-if="!disableBtn"
        class="
          inline-flex
          items-center
          px-6
          py-2
          text-sm text-gray-800
          rounded-lg
          shadow
          outline-none
          gap-x-1
          hover:bg-gray-100
        "
      >
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-left h-6 mr-2" viewBox="0 0 16 16">
          <path fill-rule="evenodd" d="M15 8a.5.5 0 0 0-.5-.5H2.707l3.147-3.146a.5.5 0 1 0-.708-.708l-4 4a.5.5 0 0 0 0 .708l4 4a.5.5 0 0 0 .708-.708L2.707 8.5H14.5A.5.5 0 0 0 15 8z"/>
        </svg>
        Nazad
      </button>
      <button
        @click="nextStep"
        class="
          px-6
          py-2
          text-sm text-white
          bg-indigo-500
          rounded-lg
          outline-none
          hover:bg-indigo-600
          ring-indigo-300
          flex
          items-center
         "
      >
        Naprijed
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-arrow-right h-6 ml-2" viewBox="0 0 16 16">
          <path fill-rule="evenodd" d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8z"/>
        </svg>
      </button>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const emit = defineEmits([
    'nextStep',
    'prevStep',
])

const props = defineProps({
  activeTab: String,
  isActive: Boolean
})

const disableBtn = computed(() => {
  return props.activeTab === 'StepOne'
})

const nextStep = () => {
  emit('nextStep')
}

const prevStep = () => {
  emit('prevStep')
}


</script>
