<template>
  <div>
    <div class="card" :class="cardColor">
      <div class="card-img">
        <img :src="foodItem.data.img" :alt="foodItem.data.name" />
      </div>
      <div class="card-info">
        <h3 class="food-name">{{ foodItem.data.name }}</h3>
        <div class="price">
          <h3>$ {{ foodItem.data.price }}</h3>
        </div>
        <h3 class="available">Available</h3>
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
.card {
  width: 192px;
  height: 226px;
  border-radius: 16px;
  background: #1f1d2b;
  border-radius: 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  margin: 50px 0px;
  color: white;
}
.card-img {
  height: 132px;
  width: 132px;
  border-radius: 50%;
  position: absolute;
  top: -20%;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}
.card-img img {
  height: 100%;
}
.card-info {
  position: absolute;
  width: 144px;
  height: 88px;
  margin-top: 112px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  font-family: "Roboto", sans-serif;
}
.food-name {
  color: whitesmoke;
  position: static;
  color: rgb(255, 255, 255);
  font-size: 14px;
  font-weight: 500;
}
.price {
  margin-top: 15px;
  font-size: 13.5px;
  margin-bottom: 10px;
}

h3.available {
  color: rgb(171, 187, 194);
  font-size: 13.5px;
  font-weight: 400;
  line-height: 140%;
  letter-spacing: 0%;
  text-align: center;
}
</style>
