<template>
  <div>
    <nav id="Navbar">
      <div class="logo_mobile_button_container">
        <div class="logo">
          <img src="../assets/logo/logo.svg" alt="logo" />
          <h3>Picante´s</h3>
        </div>
        <div class="mobile-button">
          <span v-if="menuIsClosed" v-on:click="openNav"
            ><i class="fas fa-bars"></i
          ></span>
          <span v-if="!menuIsClosed" class="exit" v-on:click="closeNav"
            ><i class="fas fa-times"></i
          ></span>
        </div>
      </div>
      <div class="links">
        <a href="#menu" v-on:click="closeNav">Menu</a>
        <a href="#about-us" v-on:click="closeNav">About Us</a>
        <a href="#contactUs" v-on:click="closeNav">Contact Us</a>
      </div>
    </nav>
  </div>
</template>
<script>
export default {
  name: "Navbar",
  data() {
    return {
      menuIsClosed: true, // if the menu is close the status is going to be true
    };
  },
  created() {
    let initialScroll = window.pageYOffset;
    window.onscroll = function() {
      let currentScroll = window.pageYOffset;
      if (initialScroll <= currentScroll) {
        document.getElementById("Navbar").style.top = "-1000px";
      } else {
        document.getElementById("Navbar").style.top = "0px";
        document.getElementById("Navbar").style.transition = ".5s";
      }
      initialScroll = currentScroll;
    };
  },
  methods: {
    closeNav() {
      document.getElementById("Navbar").classList.remove("open");
      this.menuIsClosed = true;
    },
    openNav() {
      document.getElementById("Navbar").classList.add("open");
      this.menuIsClosed = false;
    },
  },
};
</script>
<style scoped lang="css">
@import url("https://fonts.googleapis.com/css2?family=Monoton&display=swap");
#Navbar {
  font-family: "monoton";
  height: 100px;
  width: 100%;
  background-color: white;
  box-shadow: 0px 3px 5px 0px rgba(105, 75, 75, 0.1);
  display: flex;
  transition: 0.5s;
  position: fixed;
  top: 0;
}
.logo_mobile_button_container {
  width: 35%;
}
.logo {
  width: 100%;
}
.logo,
.links {
  font-family: "monoton";
  height: 100px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  color: black;
  white-space: nowrap;
}
.logo img {
  height: 80%;
}
.links {
  height: 100px;
  width: 75%;
}
.links a {
  font-weight: 600;
}
.links a,
.links h3 {
  font-size: 1.7rem;
  text-decoration: none;
  transition: 0.5s;
  color: black;
}
.links a:hover,
.links h3:hover {
  transform: translateY(-10px);
  cursor: pointer;
}
.mobile-button span i {
  font-size: 30px;
}
.mobile-button,
.exit {
  display: none;
}
@media screen and (max-width: 1024px) {
  #Navbar {
    height: 100px;
    flex-direction: column;
    overflow: hidden;
  }
  #Navbar.open {
    height: 300px;
    white-space: nowrap;
  }
  .logo_mobile_button_container {
    height: 100px;
    width: 100%;
    display: flex;
    box-shadow: 0px 3px 5px 0px rgba(105, 75, 75, 0.1);
  }
  .logo {
    width: 70%;
  }
  .links {
    height: 250px;
    width: 100%;
    flex-direction: column;
  }
  .mobile-button {
    height: 100%;
    width: 30%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .exit {
    display: initial;
  }
}
</style>
