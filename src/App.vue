<template>
  <div class="flex m-4 rounded-2xl overflow-hidden">
    <div class="w-1/3 bg-red-200">

    </div>

    <div class="w-1/3 flex flex-col items-center p-2">
      <div class="w-full text-6xl text-center">
        <div class="text-sm text-gray-300">
          21.07.2025.
        </div>
        <div>
          2:0
        </div>
      </div>
      <div>
        {{currentTime}}
      </div>
    </div>

    <div class="w-1/3 bg-blue-200">

    </div>
  </div>

  <div class="flex m-4 bg-green-400 rounded-2xl overflow-hidden">
    <div class="w-1/2 bg-yellow-200 border-r-2">
      <div class="flex flex-col text-center p-2">
        <span class="">Milos Ruzic ⚽ 1'</span>
        <span>Ivan Stojkovic ⚽ 4'</span>
        <span>Dario Jusovic ⚽ 7'</span>
        <span>Milan Brankovic ⚽ 12'</span>
        <span>Nemanja Karan ⚽ 16' </span>
      </div>
    </div>
    <div class="w-1/2 bg-purple-200">
    </div>
  </div>


  <div class="flex m-4 rounded-2xl overflow-hidden h-16">
    <div class="w-1/2 rounded-2xl overflow-hidden">
      <div class="flex flex-col p-2">
        <button
            class="bg-blue-300 text-white font-medium py-2 rounded"
        >
          ➕ Add Goal
        </button>
      </div>
    </div>
    <div class="w-1/2 rounded-2xl">
      <div class="flex flex-col p-2">
        <button
            class="bg-blue-300 text-white font-medium py-2 rounded"
        >
          ➕ Add Goal
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const currentTime = ref(getFormattedTime())
let intervalId = null

function getFormattedTime() {
  const now = new Date()
  return now.toLocaleTimeString('en-GB', {
    hour: '2-digit',
    minute: '2-digit',
    second: '2-digit',
  })
}

onMounted(() => {
  intervalId = setInterval(() => {
    currentTime.value = getFormattedTime()
  }, 1000)
})

onBeforeUnmount(() => {
  clearInterval(intervalId)
})
</script>
