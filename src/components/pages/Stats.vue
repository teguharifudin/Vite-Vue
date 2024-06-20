<template>
  <div class="px-4 mx-auto sm:max-w-xl md:max-w-full lg:max-w-screen-xl py-8">
    <div class="grid gap-8 lg:grid-cols-5 grid-cols-3">
      <div v-for="(stat, index) in stats" :key="index" class="text-center">
        <div
          class="flex items-center justify-center w-10 h-10 mx-auto mb-3 rounded-full bg-indigo-50 sm:w-12 sm:h-12"
        >
          <svg
            class="w-8 h-8 text-deep-purple-accent-400 sm:w-10 sm:h-10"
            stroke="currentColor"
            viewBox="0 0 52 52"
          >
            <polygon
              stroke-width="3"
              stroke-linecap="round"
              stroke-linejoin="round"
              fill="none"
              points="29 13 14 29 25 29 23 39 38 23 27 23"
            ></polygon>
          </svg>
        </div>
        <h6 class="text-4xl font-bold text-deep-purple-accent-400">
          {{ stat.count }}
        </h6>
        <p class="text-gray-700">
          {{ stat.name }}
        </p>
      </div>
    </div>
  </div>
</template>
  
<script setup>
const stats = [
  {
    name: "Projects Completed",
    icone: "",
    count: 3123,
  },
  {
    name: "Happy Client",
    icone: "",
    count: 4233,
  },
  {
    name: "Design Awards",
    icone: "",
    count: 1312,
  },
  {
    name: "Cups Of Coffee",
    icone: "",
    count: 1234,
  },
  {
    name: "Fast Support",
    icone: "",
    count: 6432,
  },
];
</script>