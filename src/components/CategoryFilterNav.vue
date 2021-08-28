<template>
  <div class="categoryFilterNav">
    <div
      v-for="categoryItem in category_items"
      :key="categoryItem.data.name"
      class="category-item"
      :id="categoryItem.data.name"
      v-on:click="categoryActive(categoryItem.data.name)"
    >
      <img :src="categoryItem.data.img" :alt="categoryItem.data.name" />
      <h3>{{ categoryItem.data.name }}</h3>
    </div>
  </div>
</template>
<script>
export default {
  name: "CategoryFilterNav",
  data() {
    return {
      currentCategory: "all",
    };
  },
  props: {
    category_items: null, // this prop comes from Category.vue component you can search <CategoryItem/> tag
  },
  methods: {
    categoryActive(id) {
      // this method receives the id and is going to take all the items and save it in an array
      // the id is the name of the category selected by the user
      let array = document.querySelectorAll(".category-item");
      array.forEach((element) => {
        // here we remove the active class from the items one by one
        element.classList.remove("active");
      });
      document.getElementById(id).classList.add("active"); // here we get the element with the id and add the class active
      this.$emit("filterByCategory", id); // here we emit the event to filter the food
      // this event is going to be used in component Category.vue you can search <CategoryItem/> tag
    },
  },
};
</script>
<style scope lang="css">
.categoryFilterNav {
  min-height: 100px;
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  flex-wrap: wrap;
}
.category-item {
  height: 90px;
  width: 100px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  border-bottom: 3px solid transparent;
  transition: 0.5s;
}
.category-item img {
  height: 50%;
}
.category-item.active {
  border-color: black;
}
.category-item:hover {
  cursor: pointer;
  transform: translateY(-10px);
}

</style>
