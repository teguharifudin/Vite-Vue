<script setup>
import Footer from "./Footer.vue";
import Navigation from "./Navigation.vue";
</script>

<template>
  <Navigation />
     <slot></slot>
  <Footer />
</template>