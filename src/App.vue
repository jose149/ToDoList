<script setup lang="ts">
import Todo from "./components/Todo.vue";
</script>

<template id="app">
  <!-- <Navbar id="navbar" /> -->
  <Todo id="todo" />
  <div id="footer">
    <p>@ <span class="highlight">Jose Crespi</span> 2023</p>
  </div>
</template>

<style lang="scss">
@import "@/styles/_variables.scss";

body {
  margin: 0;
  box-sizing: border-box;
  overflow: hidden;
}
p {
  margin: 0;
}
#app {
  background-color: $background-1;
  font-family: $font-family;
  display: flex;
  flex-direction: column;

  #navbar {
    width: 100vw;
    height: 10vh;
  }

  #todo {
    max-width: 885px;
    height: calc(95vh - 111px);
    margin: 0 auto 20px;
    padding-top: 60px;
    @media only screen and (max-width: $medium-breackpoint) {
      height: calc(90vh);
      margin-bottom: 0;
    }
  }

  #footer {
    padding: 30px;
    box-sizing: border-box;
    width: 100%;
    background-color: #1d1d1d;
    cursor: default;
    p {
      font-size: $font-size-small-desktop;
      color: white;
      text-align: center;
    }
    @media only screen and (max-width: $medium-breackpoint) {
      display: none;
    }
    .highlight {
      color: $primary;
    }
  }
  /* Scrollbar */
  ::-webkit-scrollbar {
    width: 6px;
  }
  ::-webkit-scrollbar-thumb {
    background: $secondary-text;
    border-radius: 6px;
  }
  /* Selection */
  ::-moz-selection {
    color: $primary-text;
    background-color: $primary;
  }
  ::selection {
    color: $primary-text;
    background-color: $primary;
  }
}
</style>
