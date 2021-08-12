<template>
  <div class="home">
    <section id="main">
      <div class="navbar-container">
        <Navbar id="Navbar" />
      </div>
      <div class="info-container">
        <img src="../assets/skull-flag-1.png" alt="skull-flag-1" />
        <h3>There’s no place like Picante´s</h3>
        <img src="../assets/skull-flag-2.png" alt="skull-flag-2" />
      </div>
    </section>
    <section class="category" id="menu">
      <Category :categoryItems="this.categories" />
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320">
        <path
          fill="#ffebcd"
          fill-opacity="1"
          d="M0,224L48,202.7C96,181,192,139,288,154.7C384,171,480,245,576,261.3C672,277,768,235,864,186.7C960,139,1056,85,1152,90.7C1248,96,1344,160,1392,192L1440,224L1440,0L1392,0C1344,0,1248,0,1152,0C1056,0,960,0,864,0C768,0,672,0,576,0C480,0,384,0,288,0C192,0,96,0,48,0L0,0Z"
        ></path>
      </svg>
    </section>
  </div>
</template>
<script>
import Navbar from "../components/Navbar.vue";
import Category from "../components/Category.vue";
//firebase
import firebase from "firebase";
import db from "../dbFirebase/db.js";
firebase.initializeApp(db);
const dataBase = firebase.firestore();
const colection = dataBase.collection("foodCategory");
export default {
  name: "Home",
  components: {
    Navbar,
    Category,
  },
  data() {
    return {
      categories: [],
    };
  },
  mounted() {
    this.getCartegories();
  },
  methods: {
    getCartegories() {
      colection
        .get()
        .then((response) =>
          response.docs.map((item) =>
            this.categories.push({ id: item.id, data: item.data() })
          )
        );
    },
  },
};
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Monoton&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Bangers&display=swap");
#Navbar {
  position: fixed;
  width: 100%;
  top: 0;
}
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
  position: relative;
  z-index: 5;
}
.info-container {
  height: 90%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}
.info-container img {
  height: 30%;
}
h3 {
  font-size: 3.5rem;
  color: black;
  font-family: "Bangers";
}
@media screen and (max-width: 1280px) {
  .info-container img {
    height: auto;
    width: 90%;
  }
  h3 {
    width: 90%;
  }
}
@media screen and (min-width: 320px) and (max-width: 320px) and (orientation: portrait) {
  h3 {
    font-size: 1.5rem;
  }
}
@media screen and (max-width: 1280px) and (orientation: landscape) {
  .info-container img {
    display: none;
  }
  h3 {
    margin-top: 50px;
    font-size: 3rem;
  }
}
</style>
