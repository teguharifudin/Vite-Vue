<template>
  <Section>
    <template v-slot:title> Our Latest News </template>
    <template v-slot:body>
      There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration, by injected humour, or new randomised words.
    </template>
    <div class="max-w-lg mx-auto grid gap-5 lg:grid-cols-3 lg:max-w-none">
      <div
        v-for="article in articles"
        :key="article.title"
        class="flex flex-col rounded-lg shadow-lg overflow-hidden"
      >
        <div class="flex-shrink-0">
          <img class="h-48 w-full object-cover" :src="'https://www.teguharief.com/uploads/'+article.imageUrl" alt="" />
        </div>
        <div class="flex-1 bg-white p-6 flex flex-col justify-between">
          <div class="flex-1">
            <p class="text-sm font-medium text-indigo-600">
                {{ article.newsSite }}
            </p>
            <a :href="article.href" class="block mt-2">
              <p class="text-xl font-semibold text-gray-900">
                {{ article.title }}
              </p>
              <p class="mt-3 text-base text-gray-500">
                {{ article.description }}
              </p>
            </a>
          </div>
          <div class="mt-6 flex items-center">
            <a :href="'https://www.teguharief.com/blog/'+article.url">
              <Button> Read More </Button>
            </a>
          </div>
        </div>
      </div>
    </div>
  </Section>
</template>
  
<script>
import Button from "../Button.vue";
import Section from "../layout/Section.vue";

export default {
  components: {
    Button,
    Section,
  },
  data() {
    return {
      articles: [],
    };
  },
  created() {
    fetch("https://www.teguharief.com/api/posts")
      .then((res) => res.json())
      .then((data) => {
        this.articles = data;
      })
      .catch((err) => console.log(err));
  },
};
</script>