<template>
  <div>
    <div class="card" :class="cardColor">
      <div class="card-img">
        <img :src="foodItem.data.img" :alt="foodItem.data.name" />
      </div>
      <div class="card-info">
        <h3 class="food-name">{{ foodItem.data.name }}</h3>
        <div class="price">
          <h3 class="price-letters">Price</h3>
          <h3>$ {{ foodItem.data.price }}</h3>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",
  props: {
    cardColor: String,
    foodItem: null, // this prop comes from Category.vue component
  },
};
</script>
<style scoped lang="css">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap");
.card.firstColor {
  background-color: #ea964e;
}
.card.secondColor {
  background-color: #4f848a;
}
.card {
  height: 220px;
  width: 200px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  margin: 50px 0px;
  color: white;
  box-shadow: rgba(0, 0, 0, 0.4) 0px 2px 4px,
    rgba(0, 0, 0, 0.3) 0px 7px 13px -3px, rgba(0, 0, 0, 0.2) 0px -3px 0px inset;
}
.card-img {
  height: 150px;
  width: 150px;
  border-radius: 50%;
  border: 10px solid white;
  position: absolute;
  top: -20%;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
.card-img img {
  height: 100%;
}
.card-info {
  height: 100px;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  position: absolute;
  bottom: 0;
}
.food-name {
  width: 90%;
  color: whitesmoke;
}
.price {
  width: 70%;
  font-family: "Roboto", sans-serif;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  color: white;
}
.price-letters {
  color: black;
}
</style>
