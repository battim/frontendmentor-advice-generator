<template>
  <section class="advice">
    <div class="advice-container">
      <p class="heading">Advice #{{ getAdvice.quoteNumber }}</p>
      <p class="quote">{{ getAdvice.quote }}</p>
      <div v-if="isMobile()">
        <img src="../assets/pattern-divider-mobile.svg" alt="" />
      </div>
      <div v-else>
        <img src="../assets/pattern-divider-desktop.svg" alt="" />
      </div>
      <button id="btn"></button>
    </div>
  </section>
</template>

<script>
function isMobile() {
  if (screen.width <= 760) {
    return true;
  } else {
    return false;
  }
}
</script>

<script setup>
import { onMounted, reactive } from "vue";
import axios from "axios";
import anime from "animejs";

let getAdvice = reactive({
  quote:
    "It is easy to sit up and take notice, what's difficult is getting up and taking action.",
  quoteNumber: "117",
  id: "",
});

onMounted(() => {
  const API_URL = `https://api.adviceslip.com/advice/`;

  const btn = document.querySelector("#btn");
  btn.addEventListener("click", () => {
    let index = Math.floor(Math.random() * 200);
    getAdvice.id = index;

    axios
      .get(`${API_URL}${getAdvice.id}`)
      .then((res) => {
        console.log(res);
        getAdvice.quote = res.data.slip.advice;
        getAdvice.quoteNumber = res.data.slip.id;
      })
      .catch((err) => {
        console.error(err);
      });

    anime.remove(btn);
    anime({
      targets: btn,
      rotate: ["0", "360"],
      scale: [0.8, 1],
      endDelay: 500,
      easing: "easeInOutExpo",
      loop: 1,
      direction: "alternate",
    });
  });
});
</script>
