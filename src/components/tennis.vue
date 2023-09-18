<template>
    <div>
      <h1 :class="pageTitleClass">{{ pageTitle }}</h1>
      <div v-html="htmlContent"></div>
      <img :src="imageURL" :alt="imageAlt" />
      <p>{{ message }}</p>
      <button @click="showMessage">Show Message</button>
      <p :style="messageStyle">{{ reversedMessage }}</p>
     <!-- a. v-for with an Object -->
    <ul>
      <li v-for="(value, key) in tennisessentials" :key="key">{{ key }}: {{ value }}</li>
    </ul>

    <!-- b. v-for with a Range -->
    <ul>
      <li v-for="n in 5" :key="n">Item {{ n }}</li>
    </ul>

    <!-- c. v-for on <template> -->
    <template v-for="item in tennisPlayers">
      <h2>{{ item.name }}</h2>
      <p>Rank: {{ item.rank }}</p>
    </template>

    <!-- d. v-for with v-if -->
    <ul>
      <li v-for="player in tennisPlayers" :key="player.id">
        {{ player.name }}
        <span v-if="player.isSpanish"> - Spanish</span>
      </li>
    </ul>

    <!-- e. v-for with a Component -->
    <ul>
      <tennis-player
        v-for="player in tennisPlayers"
        :key="player.id"
        :player="player"
      ></tennis-player>
    </ul>








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

  // a. v-for with an Object
const tennisEquipment = {
  racket: "KONEX ULTA LIGHT",
  balls: "yellow tennis balls",
  shoes: "Adidas Yeezy tennis boots",
};

// c. v-for on <template>
const tennisPlayers = [
  { id: 1, name: "Holger Rune", rank: 7 },
  { id: 2, name: "Calros Alcaraz", rank: 2 },
  { id: 3, name: "Aditya Singh", rank: 9 },
];

// d. v-for with v-if
const tennisPlayers = [
  { id: 1, name: "Holger Rune", isSpanish: false },
  { id: 2, name: "Calros Alcaraz", isSpanish: true },
  { id: 3, name: "Aditya Singh", is: false},
];

// e. v-for with a Component
import TennisPlayer from './TennisPlayer.vue';

const tennisPlayers = [
  { id: 1, name: "Holger Rune" },
  { id: 2, name: "Calros Alcaraz" },
  { id: 3, name: "Aditya Singh" },
];








  </script>
  
  <style scoped>
  .tennis-page-title {
    font-size: 33px;
    text-transform: uppercase;
  }
  </style>
  