<script setup>
import HeroSection from "./components/pages/HeroSection.vue";
import HowItWork from "./components/pages/HowItWork.vue";
import BlogVue from "./components/pages/Blog.vue";
import Team from "./components/pages/Team.vue";
import Stats from "./components/pages/Stats.vue";
import Price from "./components/pages/Price.vue";
import AppLayout from "./components/layout/AppLayout.vue";
import ContactUs from "./components/pages/ContactUs.vue";
</script>

<template>
  <AppLayout>
    <HeroSection />
    <HowItWork />
    <BlogVue />
    <Team />
    <Stats />
    <Price />
    <ContactUs />
  </AppLayout>
</template>