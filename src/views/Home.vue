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
      <Category
        :categoryItems="this.categories"
        :foodItems="this.foods"
        @filterActive="getValue"
      />
    </section>
<svg id="wave" style="transform:rotate(180deg); transition: 0.3s" viewBox="0 0 1440 490" version="1.1" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="sw-gradient-0" x1="0" x2="0" y1="1" y2="0"><stop stop-color="rgba(255, 235, 205, 1)" offset="0%"></stop><stop stop-color="rgba(255, 235, 205, 1)" offset="100%"></stop></linearGradient></defs><path style="transform:translate(0, 0px); opacity:1" fill="url(#sw-gradient-0)" d="M0,0L60,24.5C120,49,240,98,360,147C480,196,600,245,720,269.5C840,294,960,294,1080,269.5C1200,245,1320,196,1440,155.2C1560,114,1680,82,1800,57.2C1920,33,2040,16,2160,16.3C2280,16,2400,33,2520,32.7C2640,33,2760,16,2880,81.7C3000,147,3120,294,3240,367.5C3360,441,3480,441,3600,408.3C3720,376,3840,310,3960,253.2C4080,196,4200,147,4320,155.2C4440,163,4560,229,4680,277.7C4800,327,4920,359,5040,359.3C5160,359,5280,327,5400,310.3C5520,294,5640,294,5760,310.3C5880,327,6000,359,6120,310.3C6240,261,6360,131,6480,73.5C6600,16,6720,33,6840,49C6960,65,7080,82,7200,106.2C7320,131,7440,163,7560,155.2C7680,147,7800,98,7920,130.7C8040,163,8160,278,8280,318.5C8400,359,8520,327,8580,310.3L8640,294L8640,490L8580,490C8520,490,8400,490,8280,490C8160,490,8040,490,7920,490C7800,490,7680,490,7560,490C7440,490,7320,490,7200,490C7080,490,6960,490,6840,490C6720,490,6600,490,6480,490C6360,490,6240,490,6120,490C6000,490,5880,490,5760,490C5640,490,5520,490,5400,490C5280,490,5160,490,5040,490C4920,490,4800,490,4680,490C4560,490,4440,490,4320,490C4200,490,4080,490,3960,490C3840,490,3720,490,3600,490C3480,490,3360,490,3240,490C3120,490,3000,490,2880,490C2760,490,2640,490,2520,490C2400,490,2280,490,2160,490C2040,490,1920,490,1800,490C1680,490,1560,490,1440,490C1320,490,1200,490,1080,490C960,490,840,490,720,490C600,490,480,490,360,490C240,490,120,490,60,490L0,490Z"></path></svg>
<section class="about-us">
  <h3>About Us</h3>
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
const colectionCategory = dataBase.collection("foodCategory");
const colectionFood = dataBase.collection("food");
export default {
  name: "Home",
  components: {
    Navbar,
    Category,
  },
  data() {
    return {
      categories: [],
      foods: [],
      filterCategoryName: "",
    };
  },
  mounted() {
    this.getCartegories();
    this.getFoods();
  },
  methods: {
    getCartegories() {
      colectionCategory
        .get()
        .then((response) => {
          response.docs.map((item) =>
            this.categories.push({ id: item.id, data: item.data() })
          );
        })
        .catch((err) => {
          console.log(err);
        });
    },
    getFoods() {
      colectionFood
        .get()
        .then((response) => {
          response.docs.map((item) =>
            this.foods.push({ id: item.id, data: item.data() })
          );
        })
        .catch((err) => {
          console.log(err);
        });
    },
    getValue(value) {
      this.filterCategoryName = value;
      this.getFoodFiltered();
    },
    getFoodFiltered() {
      this.foods = [];
      colectionFood
        .where("type", "==", this.filterCategoryName)
        .get()
        .then((response) => {
          response.docs.map((item) =>
            this.foods.push({ id: item.id, data: item.data() })
          );
        })
        .catch((err) => {
          console.log(err);
        });
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
.about-us{
  height: 500px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}
.about-us h3{
    font-family: "monoton";
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
