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
    category_item: null, // this prop comes from Category.vue component you can search <CategoryItem/> tag
  },
  methods: {
    categoryActive(id) { // this method receives the id and is going to take all the items and save it in an array
    // the id is the name of the category selected by the user
     let array =document.querySelectorAll(".category-item");
     array.forEach(element => { // here we remove the active class from the items one by one
       element.classList.remove("active");
     });
     document.getElementById(id).classList.add("active"); // here we get the element with the id and add the class active
     this.$emit("filterByCategory",id); // here we emit the event to filter the food 
     // this event is going to be used in component Category.vue you can search <CategoryItem/> tag
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
