<template>
  <div>
    <div
      class="category-item"
      :id="category_item.data.name"
      v-on:click="categoryActive(category_item.data.name)"
    >
      <img :src="category_item.data.img" :alt="category_item.data.name" />
      <h3>{{ category_item.data.name }}</h3>
    </div>
  </div>
</template>
<script>
export default {
  name: "categoryItem",
  data() {
    return {
      currentCategory: "all",
    };
  },
  props: {
    category_item: null,
  },
  methods: {
    categoryActive(id) {
     let array =document.querySelectorAll(".category-item");
     array.forEach(element => {
       element.classList.remove("active");
     });
     document.getElementById(id).classList.add("active");
     this.$emit("filterByCategory",id);
    },
  },
};
</script>
<style scope lang="scss">
.category-item {
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.category-item.active {
  border-color: black;
}
.category-item:hover {
  cursor: pointer;
  transform: translateY(-10px);
}
.category-item {
  height: 100px;
  width: 100px;
  flex-direction: column;
  border-bottom: 3px solid transparent;
  transition: 0.5s;
}
.category-item img {
  height: 50%;
}
</style>
