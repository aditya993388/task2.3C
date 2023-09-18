<template>
    <div>
      <h1>{{ pageTitle }}</h1>
      <div v-html="htmlContent"></div>
      <img :src="imageURL" :alt="imageAlt" />
      <p>{{ message }}</p>
      <button @click="showMessage">Show Message</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const pageTitle = ref("All about Tennis");
  const htmlContent = ref("<p>We will learn the basics of Tennis</p>");
  const imageURL = ref("C:\\Users\\rayfa\\OneDrive\\Pictures\\Saved Pictures\\tennis_image.jpeg");
  const imageAlt = ref("Cool Tennis Image");
  const message = ref("");
  
  const showMessage = () => {
    message.value = "Are you excited to learn about tennis?";
  };
  </script>
  