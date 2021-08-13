<template>
  <div>
    <div class="category">
      <div
        v-for="category in categoryItems"
        :key="category.id"
        class="category-item"
        :id="category.data.name"
        v-on:click="categoryActive(category.data.name)"
      >
        <img :src="category.data.img" :alt="category.data.name" />
        <h3>{{ category.data.name }}</h3>
      </div>
      <div
        style="width: 100%; min-height: 150px; display: flex; justify-content: center; align-items: center; padding: 50px;"
      >
        <details>
          <summary>Sort By Price</summary>
          <ul>
            <li v-on:click="orderByPriceLowToHigh">Low To High</li>
            <li v-on:click="orderByPriceHighToLow">High To Low</li>
          </ul>
        </details>
      </div>
      <div class="food-container">
        <div class="card" v-for="food in foodItems" :key="food.id">
          <div class="card-img">
            <img :src="food.data.img" :alt="food.data.name" />
          </div>
          <div class="card-info">
            <h3>{{ food.data.name }}</h3>
            <h2>Price: ${{ food.data.price }}</h2>
          </div>
        </div>
        <div v-if="foodItems.length <= 0" class="lds-ellipsis">
          <div></div>
          <div></div>
          <div></div>
          <div></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Category",
  props: {
    categoryItems: null,
    foodItems: null,
  },
  data() {
    return {
      currentCategory: "",
    };
  },
  methods: {
    categoryActive(id) {
      if (this.currentCategory == "") {
        this.currentCategory = id;
        document.getElementById(id).classList.add("active");
        this.filterCategory(id);
      } else {
        document
          .getElementById(this.currentCategory)
          .classList.remove("active");
        document.getElementById(id).classList.add("active");
        this.currentCategory = id;
        this.filterCategory(id);
      }
    },
    filterCategory(id) {
      this.$emit("filterActive", id);
    },
    orderByPriceLowToHigh() {
      let newArray = this.foodItems.sort(
        (a, b) => parseFloat(a.data.price) - parseFloat(b.data.price)
      );
      this.foodItems = [];
      this.foodItems = newArray;
    },
    orderByPriceHighToLow(){
     let newArray = this.foodItems.sort((a, b) => parseFloat(b.data.price) - parseFloat(a.data.price));
     this.foodItems = [];
     this.foodItems = newArray;
    }
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
.category,
.category-item {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.category-item:hover {
  cursor: pointer;
  transform: translateY(-10px);
}
.category {
  min-height: 100px;
  height: 100%;
  width: 100%;
  background-color: blanchedalmond;
  flex-wrap: wrap;
}
.category-item {
  height: 100px;
  width: 100px;
  flex-direction: column;
  border-bottom: 3px solid transparent;
  transition: 0.5s;
}
.category-item.active {
  border-color: black;
}
.category-item img {
  height: 50%;
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
.card {
  height: 250px;
  width: 200px;
  background-color: white;
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
    rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;
  border-radius: 10px;
  overflow: hidden;
  margin: 10px 0px;
}
.card-img {
  height: 44%;
  width: 100%;
  overflow: hidden;
}
.card-img img {
  width: 100%;
  border-radius: 10px 10px 0 0;
}
.card-info {
  height: 56%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
}

details {
  position: relative;
  width: 300px;
  margin-right: 1rem;
}

details[open] {
  z-index: 1;
}

summary {
  padding: 1rem;
  cursor: pointer;
  border-radius: 5px;
  background-color: white;
  list-style: none;
}

summary::-webkit-details-marker {
  display: none;
}

details[open] summary:before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background: transparent;
  position: fixed;
  top: 0;
  left: 0;
}

summary:after {
  content: "";
  display: inline-block;
  float: right;
  width: 0.5rem;
  height: 0.5rem;
  border-bottom: 1px solid currentColor;
  border-left: 1px solid currentColor;
  border-bottom-left-radius: 2px;
  transform: rotate(45deg) translate(50%, 0%);
  transform-origin: center center;
  transition: transform ease-in-out 100ms;
}

summary:focus {
  outline: none;
}

details[open] summary:after {
  transform: rotate(-45deg) translate(0%, 0%);
}

ul {
  width: 100%;
  background: #ddd;
  position: absolute;
  top: calc(100% + 0.5rem);
  left: 0;
  padding: 1rem;
  margin: 0;
  box-sizing: border-box;
  border-radius: 5px;
  max-height: 200px;
  overflow-y: auto;
  background-color: white;
}

li {
  margin: 0;
  padding: 1rem 0;
  border-bottom: 1px solid #ccc;
  list-style: none;
  background-color: white;
  display: flex;
  justify-content: flex-start;
  transition: 0.5s;
}
li:hover {
  cursor: pointer;
  color: #3342aa;
}
li:first-child {
  padding-top: 0;
}

li:last-child {
  padding-bottom: 0;
  border-bottom: none;
}
.lds-ellipsis {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-ellipsis div {
  position: absolute;
  top: 33px;
  width: 13px;
  height: 13px;
  border-radius: 50%;
  background: black;
  animation-timing-function: cubic-bezier(0, 1, 1, 0);
}
.lds-ellipsis div:nth-child(1) {
  left: 8px;
  animation: lds-ellipsis1 0.6s infinite;
}
.lds-ellipsis div:nth-child(2) {
  left: 8px;
  animation: lds-ellipsis2 0.6s infinite;
}
.lds-ellipsis div:nth-child(3) {
  left: 32px;
  animation: lds-ellipsis2 0.6s infinite;
}
.lds-ellipsis div:nth-child(4) {
  left: 56px;
  animation: lds-ellipsis3 0.6s infinite;
}
@keyframes lds-ellipsis1 {
  0% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}
@keyframes lds-ellipsis3 {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(0);
  }
}
@keyframes lds-ellipsis2 {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(24px, 0);
  }
}
</style>
