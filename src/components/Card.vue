<template>
  <div>
    <div class="card">
      <div class="card-img">
        <img :src="foodItem.data.img" :alt="foodItem.data.name" />
      </div>
      <div class="card-info">
        <h3 class="food-name">{{ foodItem.data.name }}</h3>
        <p>
          {{ foodItem.data.definition }}
        </p>
        <div class="card-price">
          <h3>Price</h3>
          <h4>${{ foodItem.data.price }}</h4>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",
  props: {
    foodItem: null, // this prop comes from Category.vue component
  },
};
</script>
<style scoped lang="css">
.card {
  height: 300px;
  width: 200px;
  background-color: #dce6fc;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  margin: 50px 0px;
  color: black;
}
.card-img {
  height: 150px;
  width: 150px;
  border-radius: 50%;
  border: 10px solid white;
  box-shadow: rgba(0, 0, 0, 0.15) 0px 5px 15px;
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
  height: 200px;
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
  color: rgba(38, 29, 86, 1);
}
.card-info p {
  width: 90%;
  color: rgba(38, 29, 86, 0.4);
}
.card-price{
  width: 70%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.card-price h3{
    color: rgba(38, 29, 86, 1);
}
.card-price h4{
    color: rgba(38, 29, 86, 0.50);
}
</style>
