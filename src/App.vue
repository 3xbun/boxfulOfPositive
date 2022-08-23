<template>
  <div class="container">
    <header>
      <h1>BOXFUL OF POSITIVITY</h1>
      <p>
        Take a break of your day and check out what our sisters around the globe
        have to tell you today!
      </p>
    </header>

    <main>
      <div class="cards">
        <div
          v-for="(message, index) in messages"
          :key="index"
          class="card"
          :class="'card-' + index"
          :style="{
            backgroundColor: message.bg,
            transform: `rotate(${message.rt}deg)`,
          }"
        >
          <p>{{ message.msg }}</p>
          <p class="author">- {{ message.author }}</p>
        </div>
      </div>
      <form @submit.prevent="addCard(msg)">
        <input
          v-model="msg"
          class="search-bar"
          type="text"
          id="text"
          placeholder="Type something positive!"
        />
      </form>
    </main>
  </div>
</template>

<script setup>
import { ref } from "vue";

const addCard = (m) => {
  const card = {
    msg: m,
    author: "Anonymous",
    bg: colors.value[Math.floor(Math.random() * colors.value.length)],
    rt: Math.floor(Math.random() * (3 - -3 + 1) + -3),
  };

  messages.value.push(card);

  msg.value = "";
};

const colors = ref([
  "#df8c0c",
  "#f0eb8d",
  "#ad84b5",
  "#a7c967",
  "#dd91b7",
  "#7dc4ea",
]);

const msg = ref("");

const messages = ref([
  {
    msg: "Here a nice day",
    author: "Angie",
    bg: "#a7c967",
    rt: "-2",
  },
  {
    msg: "Don't forget to smile :)",
    author: "Anonymouse",
    bg: "#df8c0c",
    rt: "1",
  },
  {
    msg: "Have a good weekend girls!",
    author: "Mrs. Sama",
    bg: "#f0eb8d",
    rt: "0",
  },
  {
    msg: "Hope everyone's day is going well",
    author: "Pat",
    bg: "#ad84b5",
    rt: "1",
  },
]);
</script>
