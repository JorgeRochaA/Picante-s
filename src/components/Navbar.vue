<template>
  <div>
    <nav id="Navbar">
      <div class="logo">
        <img src="../assets/logo/logo.svg" alt="logo" />
        <h3>Picante´s</h3>
      </div>
      <div class="links" id="links">
        <a href="#menu" v-on:click="closeNav">Menu</a>
        <a href="#about-us" v-on:click="closeNav">About Us</a>
        <a href="#contactUs" v-on:click="closeNav">Contact Us</a>
      </div>
      <div class="mobile-button">
        <span v-if="menuIsClosed" v-on:click="openNav"
          ><i class="fas fa-bars"></i
        ></span>
        <span v-if="!menuIsClosed" class="exit" v-on:click="closeNav"
          ><i class="fas fa-times"></i
        ></span>
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
    function mobileOrientation() {
      switch (window.orientation) {
        case -90:
        case 90:
          document.getElementById("links").style.top = "30%";
          break;
        default:
          document.getElementById("links").style.top = "13%";
          break;
      }
    }
    window.addEventListener("orientationchange", mobileOrientation);
    let initialScroll = window.pageYOffset;
    window.onscroll = function () {
      let currentScroll = window.pageYOffset;
      if (initialScroll <= currentScroll) {
        document.getElementById("Navbar").style.top = "-1000px";
        document.getElementById("links").style.top = "-1000px";
      } else {
        document.getElementById("Navbar").style.top = "0px";
        mobileOrientation();
        document.getElementById("Navbar").style.transition = ".5s";
      }
      initialScroll = currentScroll;
    };
  },
  methods: {
    openNav() {
      document.getElementById("links").classList.add("open");
      this.menuIsClosed = false;
    },
    closeNav() {
      document.getElementById("links").classList.remove("open");
      this.menuIsClosed = true;
    },
  },
};
</script>
<style scoped lang="css">
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
  color: black;
  white-space: nowrap;
}
.logo {
  width: 25%;
}
.links {
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
.mobile-button,
.exit {
  display: none;
}
@media screen and (max-width: 1024px) {
  .logo img {
    height: 50%;
  }
  .logo {
    width: 70%;
    font-size: 0.9rem;
    justify-content: flex-start;
  }
  .logo img {
    margin-left: 30px;
  }
  .logo h3 {
    margin-left: 10px;
  }
  .links {
    height: 0;
    width: 100%;
    position: fixed;
    z-index: 1;
    top: 13%;
    left: 0;
    background-color: white;
    overflow-x: hidden;
    transition: 0.5s;
    justify-content: space-evenly;
    flex-direction: column;
    color: black;
    background-size: cover;
    background-position: center;
  }
  .links a {
    color: black;
  }
  .links.open {
    height: 40vh;
    transition: 0.5s;
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
@media screen and (max-width: 1024px) and (orientation: landscape) {
  .links {
    top: 30%;
  }
}
</style>
