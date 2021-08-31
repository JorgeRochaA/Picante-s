<template>
  <div class="footer">
    <div class="footer-img-container"></div>
    <div class="footer-info">
      <div class="social-media">
        <div class="contact-info">
          <div class="contact-item">
            <a href="#"><i class="fas fa-map-marker-alt"></i></a>
            <h5 class="mobileFooterItem">2350 Bagby St Houston Texas, USA</h5>
            <h5>Visit Us</h5>
          </div>
          <div class="contact-item">
            <a href="#"><i class="fas fa-phone-alt"></i></a>
            <h5 class="mobileFooterItem">+1 409-440-4645</h5>
            <h5>Call Us</h5>
          </div>
          <div class="contact-item">
            <a href="#"><i class="fas fa-envelope"></i></a>
            <h5 class="mobileFooterItem">picantes.retaurante@gmail.com</h5>
            <h5>Send Email</h5>
          </div>
        </div>
        <div class="social-links-container">
          <div class="social-links">
            <a href="#"><i class="fab fa-facebook-f"></i></a>
            <h5>facebook</h5>
          </div>
          <div class="social-links">
            <a href="#"><i class="fab fa-twitter"></i></a>
            <h5>Twitter</h5>
          </div>
          <div class="social-links">
            <a href="#"><i class="fab fa-instagram"></i></a>
            <h5>Instagram</h5>
          </div>
        </div>
      </div>
      <div class="copyright">
        <h4>Copyright © 2021 Picante´s. All Rights Reserved</h4>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Footer",
};
</script>
<style scoped>
.footer {
  height: 900px;
  width: 100%;
}
.footer-img-container {
  height: 60%;
  background-image: url("../assets/footer-banner.jpg");
  background-size: cover;
  background-position: center;
}
.footer-info {
  height: 40%;
  background-color: #d08559;
  display: grid;
  grid-template-areas:
    "social-media"
    "copyright";
  color: #33383b;
  font-size: 1.2rem;
}
.contact {
  grid-area: contact;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  color: #332e30;
}
.contact-info,
.social-links-container {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}
.social-links {
  display: flex;
  align-items: center;
}
.contact-item {
  display: flex;
  align-items: center;
}
.contact-item a,
.social-links a {
  height: 50px;
  width: 50px;
  margin-right: 10px;
  background-color: #33383b;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 20px;
  border-radius: 50%;
  color: white;
}
.social-links a,
.contact-item a {
  text-decoration: none;
  transition: 0.5s;
}
.social-links a:hover,
.contact-item a:hover {
  background-color: transparent;
}
.social-media {
  grid-area: social-media;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.copyright {
  grid-area: copyright;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
@media screen and (max-width: 767px) and (orientation: portrait) {
  .mobileFooterItem{
    display: none;
  }
  .copyright{
    width: 90%;
    justify-self: center;
    align-self: center;
  }
}
@media screen and (min-width: 100px) and (orientation: landscape) {
  .contact-item h5:nth-child(3){
    display: none;
  }
}
</style>
