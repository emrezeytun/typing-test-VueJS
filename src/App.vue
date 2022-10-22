<template>
  <div id="app">
    <Container />
  </div>
</template>

<script>
import Container from "@/components/Container";
export default {
  name: "App",
  components: { Container },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;1,100;1,300;1,400;1,500;1,700&display=swap');
#app {
  font-family: 'Roboto', sans-serif;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #1895a8;
}
</style>
