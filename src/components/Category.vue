<template>
  <div>
    <div class="category">
      <CategoryItem
        v-for="categoryItem in categoryItems"
        :key="categoryItem.data.id"
        :category_item="categoryItem"
        @filterByCategory="filterCategory"
      />
      <Sort class="sort" @sortByPrice="orderFoodByPrice" />
      <div class="food-container">
        <Card v-for="food in foodItems" :key="food.data.id" :foodItem="food" />
        <Loading v-if="foodItems.length <= 0" />
      </div>
    </div>
  </div>
</template>
<script>
import CategoryItem from "../components/categoryItem.vue";
import Card from "../components/Card.vue";
import Loading from "../components/Loading.vue";
import Sort from "../components/Sort.vue";
export default {
  name: "Category",
  components: {
    CategoryItem,
    Card,
    Loading,
    Sort,
  },
  props: {
    categoryItems: null,
    foodItems: null,
  },
  data() {
    return {
      currentCategory: "",
      sortValue: "",
    };
  },
  methods: {
    filterCategory(id) {
      this.$emit("filterActive", id);
    },
    orderFoodByPrice(id) {
      if (id == "LowToHigh") {
        let newArray = this.foodItems.sort(
          (a, b) => parseFloat(a.data.price) - parseFloat(b.data.price)
        );
        id = newArray;
      } else if (id == "HighToLow") {
        let newArray = this.foodItems.sort(
          (a, b) => parseFloat(b.data.price) - parseFloat(a.data.price)
        );
        this.foodItems = newArray;
      } else {
        console.log("error in sort");
      }
    },
  },
};
</script>
<style scoped lang="scss">
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
  background-color: blanchedalmond;
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
  min-height: 100px;
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-wrap: wrap;
}
</style>
