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
      <div class="food-container"></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Category",
  props: {
    categoryItems: null,
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
      } else {
        document
          .getElementById(this.currentCategory)
          .classList.remove("active");
        document.getElementById(id).classList.add("active");
        this.currentCategory = id;
      }
    },
  },
};
</script>
<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Monoton&display=swap");
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
  animation: move 2s ease 0s 1 normal forwards;
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
  height: 500px;
  width: 100%;
  background-color: blanchedalmond;
  border-color: black;
}
@keyframes move {
  0%,
  100% {
    transform: rotate(0deg);
    transform-origin: 50% 0;
  }

  10% {
    transform: rotate(2deg);
  }

  20%,
  40%,
  60% {
    transform: rotate(-4deg);
  }

  30%,
  50%,
  70% {
    transform: rotate(4deg);
  }

  80% {
    transform: rotate(-2deg);
  }

  90% {
    transform: rotate(2deg);
  }
}
</style>
