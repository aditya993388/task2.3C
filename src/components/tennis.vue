<template>
    <div>
      <h1 :class="pageTitleClass">{{ pageTitle }}</h1>
      <div v-html="htmlContent"></div>
      <img :src="imageURL" :alt="imageAlt" />
      <p>{{ message }}</p>
      <button @click="showMessage">Show Message</button>
      <p :style="messageStyle">{{ reversedMessage }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  
  const pageTitle = ref("All about Tennis");
  const htmlContent = ref("<p>We will learn the basics of Tennis</p>");
  const imageURL = ref("C:\\Users\\rayfa\\OneDrive\\Pictures\\Saved Pictures\\tennis_image.jpeg");
  const imageAlt = ref("Cool Tennis Image");
  const message = ref("");
  
  const showMessage = () => {
    message.value = "Are you excited to learn about tennis";
  };
  
  const reversedMessage = computed(() => {
    return message.value.split('').reverse().join('');
  });
  
  const pageTitleClass = computed(() => {
    // You can conditionally apply classes based on some logic here
    return 'tennis-is-the-best-game'; // For example, applying a class called 'tennis-page-title'
  });
  
  const messageStyle = computed(() => {
    // You can conditionally apply inline styles based on some logic here
    return {
      color: 'pink', // For example, setting the text color to blue
    };
  });
  </script>
  
  <style scoped>
  .tennis-page-title {
    font-size: 33px;
    text-transform: uppercase;
  }
  </style>
  