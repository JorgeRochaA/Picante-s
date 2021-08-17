<template>
  <div>
    <div class="card">
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
    foodItem: null, // this prop comes from Category.vue component
  },
};
</script>
<style scoped lang="css">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap');
.card {
  height: 220px;
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
  color: black;
}
.price{
  width: 70%;
 font-family: 'Roboto', sans-serif;
 display: flex;
 justify-content: space-evenly;
 align-items: center;
}
.price-letters{
  color: #dd544f;
}
</style>
