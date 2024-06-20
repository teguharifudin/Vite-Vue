<script setup>
import Button from "../Button.vue";

defineProps({
  title: String,
  price: String,
  billing: String,
  buttonText: String,
  features: Array,
  color: String,
  gradient: Boolean,
});
</script>

<template>
  <div class="p-4">
    <div
      :class="[
        'bg-white shadow-lg rounded-lg overflow-hidden group hover:bg-gray-100 transition duration-300 text-center',
        color || '',
      ]"
    >
      <div class="px-6 py-8">
        <h3
          class="text-2xl font-semibold {{ gradient ? 'text-white' : 'text-gray-800' }}"
        >
          {{ title }}
        </h3>
        <p
          class="text-4xl font-bold mt-2 {{ gradient ? 'text-white' : 'text-blue-600' }}"
        >
          {{ price }}
        </p>
        <p class="text-gray-600">{{ billing }}</p>
        <Button>{{ buttonText ?? "Get Started" }}</Button>
      </div>
      <div class="px-6 py-4 border-t border-gray-200">
        <ul class="text-gray-600">
          <li v-for="feature in features" :key="feature" class="mb-2">
            {{ feature }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>