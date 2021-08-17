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
      <CategoryFoodContainer
        :categoryItems="this.categories"
        :foodItems="this.foodsFiltered"
        @filterActive="filterFood"
      />
    </section>
    <section class="about-us" id="about-us">
      <h3>About Us</h3>
    </section>
  </div>
</template>
<script>
import Navbar from "../components/Navbar.vue";
import CategoryFoodContainer from "../components/CategoryFoodContainer.vue";
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
    CategoryFoodContainer,
  },
  data() {
    return {
      categories: [],
      foods: [],
      foodsFiltered: [],
    };
  },
  mounted() {
    this.getCategories(); // here we load the food categories and the food when the view is mounted
    this.getFoods();
  },
  methods: {
    getCategories() {
      // this method get all the categories from firebase
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
      // this method get all the food from firebase
      colectionFood
        .get()
        .then((response) => {
          response.docs.map((item) =>
            this.foods.push({ id: item.id, data: item.data() })
          );
          response.docs.map((item) =>
            this.foodsFiltered.push({ id: item.id, data: item.data() })
          );
        })
        .catch((err) => {
          console.log(err);
        });
    },
    filterFood(id){
    this.foodsFiltered = [];
    this.foods.forEach(element => {
      if (element.data.type == id) {
        setTimeout(() => {
          this.foodsFiltered.push(element);
        }, 500);
      }
    });
    },
  },
};
</script>

<style scoped lang="css">
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
.about-us {
  height: 500px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}
.about-us h3 {
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
