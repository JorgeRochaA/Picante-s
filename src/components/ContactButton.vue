<template>
  <a
    class="contact-button-container"
    href="https://api.whatsapp.com/send?phone=+50664590757&text=Hello Jorge, we would like to contact you for a project"
  >
    <h3>contact us</h3>
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
  height: 60px;
  width: 60px;
  position: fixed;
  background-color: #3db94d;
  z-index: 10;
  bottom: 0;
  right: 0;
  margin-bottom: 20px;
  margin-right: 20px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  transition: 0.5s;
  border-radius: 65px;
  overflow: hidden;
  white-space: nowrap;
  text-decoration: none;
}
.contact-button-container:hover {
  width: 180px;
  border-radius: 65px;
  cursor: pointer;
}
.button {
  position: absolute;
  right: 0;
  height: 65px;
  width: 65px;
  background-color: #0cb740;
  border-radius: 65px;
  display: flex;
  justify-content: center;
  align-items: center;
  pointer-events: none;
}
.button a i {
  font-size: 2.5rem;
  color: white;
  margin-left: 6px;
  margin-bottom: 1px;
}
</style>
