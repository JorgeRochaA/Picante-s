<template>
  <div>
    <div class="category">
      <CategoryFilterNav
        :category_items="categoryItems"
        @filterByCategory="filterCategory"
      />
      <Sort
        v-if="foodItems.length"
        class="sort"
        @sortByPrice="orderFoodByPrice"
      />
      <div class="food-container" v-if="foodItems.length">
        <Card v-for="food in foodItems" :key="food.id" :foodItem="food" />
      </div>
      
      <Loading class="loading" v-if="foodItems.length <= 0" />
    </div>
  </div>
</template>
<script>
import CategoryFilterNav from "../components/CategoryFilterNav.vue";
import Card from "./Card.vue";
import Loading from "./Loading.vue";
import Sort from "./Sort.vue";
export default {
  name: "CategoryFoodContainer",
  components: {
    CategoryFilterNav,
    Card,
    Loading,
    Sort,
  },
  props: {
    categoryItems: null, // this prop comes from the view home.vue you can search the <Category/> tag on home.vue
    foodItems: null, // this prop comes from the view home.vue you can search the <Category/> tag on home.vue
  },
  methods: {
    filterCategory(id) {
      this.$emit("filterActive", id);
    },
    orderFoodByPrice(id) {
      // this method sort the food from the array depending of the id recieved from Sort component
      if (id == "LowToHigh") {
        this.foodItems.sort(
          (a, b) => parseFloat(a.data.price) - parseFloat(b.data.price)
        );
      } else if (id == "HighToLow") {
        this.foodItems.sort(
          (a, b) => parseFloat(b.data.price) - parseFloat(a.data.price)
        );
      } else {
        console.log("error in sort");
      }
    },
  },
};
</script>
<style scoped lang="css">
@import url("https://fonts.googleapis.com/css2?family=Monoton&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Recursive&display=swap");
h2 {
  font-family: "recursive";
}
h3 {
  font-family: "monoton";
}
.category {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.category {
  min-height: 100px;
  height: 100%;
  width: 100%;
  background-color: white;
  flex-wrap: wrap;
}
.sort {
  width: 90%;
  min-height: 150px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 50px;
}
.food-container {
  min-height: 500px;
  height: 100%;
  width: 100%;
  display: grid;
  justify-content: space-evenly;
  align-items: center;
}
.loading {
  width: 100%;
  height: 300px;
}
@media screen and (min-width: 1281px) {
  .food-container {
    grid-template-columns: auto auto auto auto;
  }
}
@media screen and (min-width: 1025px) and (max-width: 1280px) {
  .food-container {
    grid-template-columns: auto auto auto auto;
  }
}
@media screen and (min-width: 768px) and (max-width: 1024px) {
  .food-container {
    grid-template-columns: auto auto auto;
  }
}

@media screen and (min-width: 768px) and (max-width: 1024px) and (orientation: horizontal) {
  .food-container {
    grid-template-columns: auto auto auto auto;
  }
}
@media screen and (min-width: 481px) and (max-width: 767px) {
  .food-container {
    grid-template-columns: auto auto;
  }
}
@media screen and (min-width: 320px) and (max-width: 480px) {
  .food-container {
    grid-template-columns: auto;
  }
}
</style>
