<template>
  <a class="contact-button-container"  href="https://api.whatsapp.com/send?phone=+50664590757&text=Hello Jorge, we would like to contact you for a project">
    <h3>Contact us</h3>
    <div class="button">
      <a><i class="fab fa-whatsapp"></i></a>
    </div>
  </a>
</template>
<script>
export default {
  name: "contactButton",
};
</script>
<style scope lang="css">
.contact-button-container h3 {
  margin-left: 20px;
  color: white;
  pointer-events: none;
}
.contact-button-container {
  height: 75px;
  width: 75px;
  position: fixed;
  background-color: #4dc247;
  z-index: 10;
  bottom: 0;
  right: 0;
  margin-bottom: 20px;
  margin-right: 20px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  transition: .5s;
  border-radius: 75px;
  overflow: hidden;
  white-space: nowrap;
  text-decoration: none;
}
.contact-button-container:hover {
  width: 200px;
  border-radius: 75px;
  cursor: pointer;
}
.button {
  position: absolute;
  right: 0;
  height: 75px;
  width: 75px;
  background-color: #4dc247;
  border-radius: 75px;
  display: flex;
  justify-content: center;
  align-items: center;
  pointer-events: none;
}
.button a i {
  font-size: 3rem;
  color: white;
}
</style>
