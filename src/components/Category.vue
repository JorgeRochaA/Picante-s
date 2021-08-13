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
      </div>
      <div class="lds-ellipsis">
        <div></div>
        <div></div>
        <div></div>
        <div></div>
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
  height: 100%;
  min-height: 300px;
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-wrap: wrap;
  background-color: whitesmoke;
}
.card {
  height: 250px;
  width: 200px;
  background-color: white;
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
    rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;
  border-radius: 10px;
  overflow: hidden;
  margin: 20px 0px;
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
