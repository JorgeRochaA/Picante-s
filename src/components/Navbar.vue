<template>
  <div>
    <nav>
      <div class="logo">
        <img src="../assets/logo/logo.svg" alt="logo" />
        <h3>Picante´s</h3>
      </div>
      <div class="links">
        <h3>Contact Us</h3>
        <a href=""><i class="fab fa-facebook"></i></a>
        <a href=""><i class="fab fa-twitter"></i></a>
        <a href=""><i class="fab fa-instagram"></i></a>
      </div>
      <div class="mobile-button">
        <span><i class="fas fa-bars"></i></span>
      </div>
    </nav>
  </div>
</template>
<script>
export default {
  name: "Navbar",
};
</script>
<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Monoton&display=swap");
nav {
  height: 100px;
  width: 100%;
  background-color: white;
  box-shadow: 0px 3px 5px 0px rgba(0, 0, 0, 0.1);
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  font-size: 1.5rem;
  font-family: "monoton";
}
nav img {
  height: 80%;
}
.logo,
.links {
  height: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.logo,
.links a {
  color: black;
}
.logo {
  width: 25%;
}
.links {
  width: 75%;
}
.links a,
.links h3 {
  font-size: 1.7rem;
  text-decoration: none;
  transition: 0.5s;
}
.links a:hover,
.links h3:hover {
  transform: translateY(-10px);
  cursor: pointer;
}
.mobile-button{
  display: none;
}
@media (min-width: 320px) and (max-width: 480px) {
  nav{
   position: relative;
   height: 500px;
   flex-direction: column;
  }
  .logo img {
    height: 50%;
  }
  .logo {
    width: 70%;
    font-size: 0.9rem;
    justify-content: space-around;
  }
  .links {
    position: absolute;
    left: 0;
    flex-direction: column;
    flex-wrap: wrap;
    background-color: firebrick;
  }
  .mobile-button{
    height: 100%;
    width: 30%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
