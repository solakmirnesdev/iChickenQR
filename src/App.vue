<template>
  <div class="mt-8">
    <h2
        class="
          mb-4
          text-2xl
          font-bold
          text-center text-gray-800
          lg:text-3xl
          md:mb-6
        "
    >
      iChicken
    </h2>

    <p class="max-w-screen-md mx-auto text-center text-gray-500 md:text-lg px-2">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. A cum id modi molestiae officiis placeat
    </p>
  </div>
  <div class="text-gray-600">
    <div class="container flex flex-col flex-wrap px-5 py-4 mx-auto">
      <div class="flex flex-wrap justify-between">
        <a
            @click="activeTab = 'StepOne'; isActive = true"
            class="
              inline-flex
              items-center
              justify-center
              w-1/2
              py-3
              font-medium
              leading-none
              tracking-wider
              sm:px-6 sm:w-auto sm:justify-start
              title-font
              border-b-2
              border-indigo-500
              text-indigo-500
            "
        >
          Korak 1
        </a>
        <a
            @click="activeTab = 'StepTwo'; isActive = false"
            :class="!isActive ? 'border-indigo-500 border-indigo-500 text-indigo-500' : ''"
            class="
              inline-flex
              items-center
              justify-center
              w-1/2
              py-3
              font-medium
              leading-none
              tracking-wider
              sm:px-6 sm:w-auto sm:justify-start
              title-font
              border-b-2
            "
        >
          Korak 2
        </a>
      </div>
      <div class="flex flex-col w-full text-center">
        <div class="py-6 bg-white sm:py-8 lg:py-12">
          <div class="px-4 mx-auto max-w-screen-2xl md:px-8">
            <div class="body">
              <StepOne
                v-if="activeTab === 'StepOne'"
                @sendCred="sendCred"
              />
              <StepTwo
                v-if="activeTab === 'StepTwo'"
                @starRating="starRating"
              />
            </div>
            <div>
              <ActionButtons
                  @nextStep="nextStep"
                  @prevStep="prevStep"
                  :activeTab="activeTab"
                  :isActive="isActive"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import StepOne from './components/StepOne.vue'
import StepTwo from './components/StepTwo.vue'
import ActionButtons from './components/ActionButtons.vue'

import { ref } from 'vue'

const activeTab = ref('StepOne')
const isActive = ref(true)
const stars = ref(0)
const cred = ref('')

const nextStep = () => {
  if (activeTab.value === 'StepOne') {
    activeTab.value = 'StepTwo'
    isActive.value = false
    console.log(activeTab.value)
  }
  else if (activeTab.value === 'StepTwo') {
    console.log('Stars value' + stars.value)
    console.log('Data' + cred.value)
  }
}

const prevStep = () => {
  if (activeTab.value === 'StepTwo') {
    activeTab.value = 'StepOne'
    isActive.value = true
  }
}

const starRating = (index) => {
  stars.value = index
}

const sendCred = (sendData) => {
  cred.value = sendData
}

</script>
