<template>
  <div class="app">
    <Quote />
  </div>
</template>

<script>
import Quote from "./components/QuoteView.vue";

export default {
  name: "App",
  components: {
    Quote,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap");
:root {
  --light-cyan: hsl(193, 38%, 86%);
  --neon-green: hsl(150, 100%, 66%);
  --grayish-blue: hsl(217, 19%, 38%);
  --dark-grayish-blue: hsl(217, 19%, 24%);
  --dark-blue: hsl(218, 23%, 16%);
}

* {
  box-sizing: border-box;
  font-family: "Manrope", sans-serif;
  margin: 0;
  padding: 0;
}

.advice {
  background-color: var(--dark-blue);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;

  &-container {
    background-color: var(--dark-grayish-blue);
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    text-align: center;
    align-items: center;
    position: relative;
    margin: 0 auto;
    padding: 40px 40px 70px;
    max-width: 550px;
    border-radius: 16px;

    .heading {
      color: var(--neon-green);
      font-size: 0.88rem;
      letter-spacing: 3px;
      margin-bottom: 2rem;
      text-transform: uppercase;
    }

    .quote {
      position: relative;
      font-size: 1.75rem;
      color: var(--light-cyan);
      margin-bottom: 2rem;

      &:before,
      &:after {
        content: '"';
        color: var(--light-cyan);
        margin: 0px 2px;
      }
    }
  }
  button {
    background: var(--neon-green) url("../src/assets/icon-dice.svg") no-repeat
      50%;
    height: 65px;
    width: 65px;
    border-radius: 50%;
    border: none;
    cursor: pointer;
    position: absolute;
    top: calc(100% - 32px);

    &:hover {
      box-shadow: 0px 0px 30px 3px var(--neon-green);
    }
  }
}
</style>
