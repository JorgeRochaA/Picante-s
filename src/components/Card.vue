<template>
    <div>
         <div class="card">
          <div class="card-img">
            <img :src="foodItem.data.img" :alt="foodItem.data.name" />
          </div>
          <div class="card-info">
            <h3>{{ foodItem.data.name }}</h3>
            <h2>Price: ${{ foodItem.data.price }}</h2>
          </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "Card",
    props:{
        foodItem: null,
    }
}
</script>
<style scoped lang="scss">
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
</style>