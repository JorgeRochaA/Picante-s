<template>
  <div class="home">
    <section id="main">
      <div class="navbar-container">
        <Navbar />
      </div>
      <div class="info-container">
        <img src="../assets/skull-flags.png" alt="skull-flags" />
        <h3>There’s no place like Picante´s</h3>
      </div>
    </section>
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
export default {
  name: "Home",
  components: {
    Navbar,
  },
};
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Monoton&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Bangers&display=swap");
#main {
  height: 100vh;
  width: 100%;
  background-image: url("../assets/banner/banner.jpg");
  background-size: contain;
  background-position-x: center;
  display: flex;
  flex-direction: column;
}
.navbar-container,
.info-container {
  width: 100%;
}
.navbar-container {
  height: 10%;
  background-color: chocolate;
}
.info-container {
  height: 90%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.info-container img {
  height: 50%;
}
h3 {
  font-size: 3.5rem;
  color: black;
  font-family: "Bangers";
}
</style>
