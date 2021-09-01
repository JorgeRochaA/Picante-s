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
      <div class="about-us-container">
        <div class="about-us-img"></div>
        <div class="about-us-text">
          <h3>About Us</h3>
          <p>
            Fancy a delicious Mexican meal? Maybe you're in the mood for some
            tacos? No matter what type of food you have in mind, Picante's
            Restaurant is ready to prepare it for you. Since 2003, Picante's
            Restaurant has been the preferred place for residents of Houston,
            Texas. Our restaurant healthy and tasty dining options, From tacos
            to pizzas, burgers, and pastas, you will find all kinds of hearty
            meals freshly prepared. We are here to serve you the best food in
            the place, whenever you are looking for a great Mexican food
            restaurant
          </p>
        </div>
      </div>
    </section>
    <section class="contact-us" id="contactUs">
      <div class="contact-us-info">
        <table>
          <tr>
            <td><img src="../assets/mapMark.svg" alt="map mark" /></td>
            <td><p>We are located in Bagby</p></td>
          </tr>
          <tr>
            <td><img src="../assets/texas.svg" alt="texas" /></td>
            <td><p>Houston, Texas, U.S.A</p></td>
          </tr>
          <tr>
            <td><img src="../assets/whatsapp.svg" alt="Whatsapp" /></td>
            <td><p>+1 409-440-4645</p></td>
          </tr>
        </table>
      </div>
      <iframe
        class="map"
        src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d13856.465164673424!2d-95.38002414754588!3d29.745347409993325!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8640b8b4488d8501%3A0xca0d02def365053b!2sHouston%2C%20Texas%2C%20EE.%20UU.!5e0!3m2!1ses!2scr!4v1630092791993!5m2!1ses!2scr"
        width="400"
        height="300"
        style="border: 0"
        allowfullscreen=""
        loading="lazy"
      ></iframe>
    </section>
    <Footer />
  </div>
</template>
<script>
import Navbar from "../components/Navbar.vue";
import CategoryFoodContainer from "../components/CategoryFoodContainer.vue";
import Footer from "../components/Footer.vue";
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
    Footer,
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
    filterFood(id) {
      this.foodsFiltered = [];
      this.foods.forEach((element) => {
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
.about-us {
  height: 700px;
  width: 100%;
}
.about-us h3 {
  font-family: "monoton";
}
.about-us-container {
  height: 100%;
  width: 100%;
  position: relative;
}
.about-us-img {
  height: 100%;
  width: 100%;
  background-image: url("../assets/about-banner.jpg");
  background-size: cover;
  background-attachment: fixed;
  background-position-x: center;
  opacity: .5;
}
.about-us-text {
  height: 100%;
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  align-items: center;
}
.about-us-text p {
  width: 80%;
  font-size: 1.3rem;
  line-height: 40px;
}
.contact-us {
  height: 600px;
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  background-image: url("../assets/location.svg");
  background-size:  contain;
  background-repeat: no-repeat;
  background-attachment: fixed;

}
table{
  height: 100%;
  width: 60%;
}
.contact-us-info {
  height: 40%;
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}
.contact-us-info h4 {
  font-size: 3rem;
  color: red;
}
.contact-us-info p {
  font-size: 1.5rem;
}
.contact-us-info img {
  height: 50px;
}
.map {
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
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
@media screen and (min-width: 100px) and (max-width: 320px) and (orientation: portrait) {
  h3 {
    font-size: 1.5rem;
  }
}
@media (min-width: 100px) and (max-width: 1024px) {
  .about-us {
    min-height: 1000px;
  }
  .about-us-img {
    height: 100%;
    width: 100%;
    background-position: center;
  }
  .about-us-text {
    height: 100%;
    width: 100%;
  }
  .about-us-text p {
    width: 90%;
    line-height: 50px;
    font-size: 1.2rem;
  }
  .contact-us {
    height: 650px;
    flex-direction: column;
  }
  table{
    width: 90%;
  }
  .contact-us-info{
    width: 100%;
  }
  .map {
    width: 90%;
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
  table{
    width: 70%;
  }
}
</style>
