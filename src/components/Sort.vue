<template>
  <div>
    <div>
      <details>
        <summary>Sort By Price</summary>
        <ul>
          <li v-on:click="sortByPrice('LowToHigh')">Low To High</li>
          <li v-on:click="sortByPrice('HighToLow')">High To Low</li>
        </ul>
      </details>
    </div>
  </div>
</template>
<script>
export default {
  name: "Sort",
  methods: {
    sortByPrice(lowOrHigh) {
      this.$emit("sortByPrice", lowOrHigh); // here we emit this event to sort the price depending of the selection from the user
      // you can search <Sort/> tag on the component Category.vue
    },
  },
};
</script>
<style scoped lang="css">
details {
  position: relative;
  width: 300px;
  margin-right: 1rem;
}

details[open] {
  z-index: 1;
}

summary {
  padding: 1rem;
  cursor: pointer;
  border-radius: 5px;
  background-color: #dce6fc;
  list-style: none;
  color: #261d56;
}

summary::-webkit-details-marker {
  display: none;
}

details[open] summary:before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background: transparent;
  position: fixed;
  top: 0;
  left: 0;
}

summary:after {
  content: "";
  display: inline-block;
  float: right;
  width: 0.5rem;
  height: 0.5rem;
  border-bottom: 1px solid currentColor;
  border-left: 1px solid currentColor;
  border-bottom-left-radius: 2px;
  transform: rotate(45deg) translate(50%, 0%);
  transform-origin: center center;
  transition: transform ease-in-out 100ms;
}

summary:focus {
  outline: none;
}

details[open] summary:after {
  transform: rotate(-45deg) translate(0%, 0%);
}

ul {
  width: 100%;
  background: #ddd;
  position: absolute;
  top: calc(100% + 0.5rem);
  left: 0;
  padding: 1rem;
  margin: 0;
  box-sizing: border-box;
  border-radius: 5px;
  max-height: 200px;
  overflow-y: auto;
  background-color: #dce6fc;
  color: #261d56;
}

li {
  margin: 0;
  padding: 1rem 0;
  border-bottom: 1px solid #ccc;
  list-style: none;
  background-color: #dce6fc;
  display: flex;
  justify-content: flex-start;
  transition: 0.5s;
}
li:hover {
  cursor: pointer;
  color: #3342aa;
}
li:first-child {
  padding-top: 0;
}

li:last-child {
  padding-bottom: 0;
  border-bottom: none;
}
</style>
