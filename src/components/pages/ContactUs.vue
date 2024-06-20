<script setup>
import InputError from "../InputError.vue";
import Button from "../Button.vue";
import TextInput from "../Input.vue";
import Status from "../Status.vue";
import { reactive, ref } from "vue";
import axios from "axios";
import { ColorSwatchIcon } from "@vue-hero-icons/outline";

const form = reactive({
  name: "",
  email: "",
  subject: "",
  message: "",
  status: "",
  errors: {
    name: "",
    email: "",
    subject: "",
    message: "",
  },
});
const clearForm = () => {
  for (const key in form) {
    if (key !== "status") {
      form[key] = "";
      form.errors[key] = "";
    }
  }
};
const clearError = () => {
  for (const key in form) {
    form.errors[key] = "";
  }
};
const handelError = (e) => {
  clearError();
  for (const key in form.errors) {
    if (e.response.data.errors[key]) {
      form.errors[key] = e.response.data.errors[key][0];
    }
  }
};
const submit = async () => {
  const formData = {
    name: form.name,
    email: form.email,
    subject: form.subject,
    message: form.message,
  };
  try {
    const response = await axios
      .post("http://127.0.0.1:8000/api/contact", formData)
      .then((response) => {
        if (response.status === 201) {
          clearForm();
          form.status =
            "We received your message and you'll hear from us soon. Thank You!";
            clearForm();
        }
        console.log(response.data);
      });
  } catch (e) {
    form.errors = e.response.data.errors;
    handelError(e);
    form.errors.name = e.response.data.errors.name;
    form.errors.email = e.response.data.errors.email;
    form.errors.subject = e.response.data.errors.subject;
    form.errors.message = e.response.data.errors.message;
    form.status = "";
    console.log(e.response.data);
  }
};
</script>

<template>
  <div
    class="relative pt-16 pb-20 px-4 sm:px-6 lg:pt-24 lg:pb-28 lg:px-8 h-screen bg-zinc-800"
  >
    <div class="absolute inset-0">
      <div class="bg-zinc-800 h-1/3 sm:h-2/3" />
    </div>
    <div class="relative max-w-7xl mx-auto">
      <div class="text-center">
        <h2
          class="text-3xl tracking-tight font-extrabold text-gray-300 sm:text-4xl"
        >
          Get In Touch
        </h2>
        <p class="mt-3 max-w-2xl mx-auto text-xl text-gray-500 sm:mt-4">
          There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration, by injected humour, or new randomised words.
        </p>
      </div>
      <form class="items-center" @submit.prevent="submit">
        <Status :message="form.status" />
        <div class="grid grid-cols-2 gap-2">
          <div>
            <div class="mt-5">
              <TextInput
                id="name"
                v-model="form.name"
                type="text"
                placeholder="Name"
                required
                autocomplete="current-name"
              />
              <InputError class="mt-2" :message="form.errors.name" />
            </div>
            <div class="mt-5">
              <TextInput
                id="email"
                v-model="form.email"
                type="email"
                placeholder="Email"
                required
                autocomplete="current-email"
              />
              <InputError class="mt-2" :message="form.errors.email" />
            </div>
            <div class="mt-5">
              <TextInput
                id="subject"
                v-model="form.subject"
                type="text"
                placeholder="Subject"
                required
                autocomplete="current-subject"
              />
              <InputError class="mt-2" :message="form.errors.subject" />
            </div>
          </div>
          <div>
            <div class="mt-5">
              <textarea
                v-model="form.message"
                id="message"
                rows="7"
                class="block p-2.5 w-full resize-none text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                placeholder="Message"
              ></textarea>
              <InputError class="mt-2" :message="form.errors.message" />
            </div>
          </div>
        </div>
        <div class="flex justify-center">
          <Button class="ml-4">Send Message</Button>
        </div>
      </form>
    </div>
  </div>
</template>