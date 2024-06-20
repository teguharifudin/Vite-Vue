<script setup>
import Section from "../layout/Section.vue";

const incentives = [
  {
    name: "Free shipping",
    imageSrc:
      "https://tailwindui.com/img/ecommerce/icons/icon-shipping-simple.svg",
    description:
      "It's not actually free we just price it into the products. Someone's paying for it, and it's not us.",
  },
  {
    name: "10-year warranty",
    imageSrc:
      "https://tailwindui.com/img/ecommerce/icons/icon-warranty-simple.svg",
    description:
      "If it breaks in the first 10 years we'll replace it. After that you're on your own though.",
  },
  {
    name: "Exchanges",
    imageSrc:
      "https://tailwindui.com/img/ecommerce/icons/icon-exchange-simple.svg",
    description:
      "If you don't like it, trade it to one of your friends for something of theirs. Don't send it here though.",
  },
];
</script>

<template>
  <Section>
    <template v-slot:title>We built our business on customer service</template>

    <template v-slot:body>
      At the beginning at least, but then we realized we could make a lot more money if we kinda stopped caring about that. Our new strategy is to write a bunch of things that look really good in the headlines, then clarify in the small print but hope people don't actually read it.
    </template>

    <div class="grid grid-cols-1 gap-y-10 gap-x-8 lg:grid-cols-3">
      <div
        v-for="incentive in incentives"
        :key="incentive.name"
        class="sm:flex lg:block inline-block mb-0 text-align: center;"
      >
        <div class="sm:flex-shrink-0">
          <img class="w-16 h-16" :src="incentive.imageSrc" alt="" />
        </div>
        <div class="mt-4 sm:mt-0 sm:ml-6 lg:mt-6 lg:ml-0">
          <h3 class="text-sm font-medium">
            {{ incentive.name }}
          </h3>
          <p class="mt-2 text-sm text-gray-500">
            {{ incentive.description }}
          </p>
        </div>
      </div>
    </div>
  </Section>
</template>