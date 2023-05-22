<template>
  <header class="header">
    <div class="burger">
      <div class="burger--inner">
        <div class="burger--header">
          <button class="close--modal">
            <svg width="34" height="34" viewBox="0 0 34 34" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M29.7499 29.7499L4.25 4.25" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M29.7501 4.25L4.25 29.7501" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </div>
        <div class="burger--main">
          <a v-scroll-to.scrollTo="{ el: '#services' }">Услуги</a>
          <a v-scroll-to.scrollTo="{ el: '#contact' }" class="burger--btn">
            <div class="btn--arrow">
              <svg width="19" height="10" viewBox="0 0 19 10" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M17.9419 5.44194C18.186 5.19786 18.186 4.80214 17.9419 4.55806L13.9645 0.580583C13.7204 0.336505 13.3247 0.336505 13.0806 0.580583C12.8365 0.82466 12.8365 1.22039 13.0806 1.46447L16.6161 5L13.0806 8.53553C12.8365 8.77961 12.8365 9.17534 13.0806 9.41942C13.3247 9.6635 13.7204 9.6635 13.9645 9.41942L17.9419 5.44194ZM0.5 5.625H17.5V4.375H0.5V5.625Z" fill="#F9FBFE"/>
              </svg>
            </div>
            Получить консультацию
          </a>
          <a a v-scroll-to.scrollTo="{ el: '#about' }">О нас</a>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="header--inner">
        <img :src="Logo" alt="Logo" class="logo">
        <nav class="nav">
          <ul>
            <li>
              <a v-scroll-to.scrollTo="{ el: '#services' }">Услуги</a>
            </li>
            <li>
              <a v-scroll-to.scrollTo="{ el: '#about' }">О нас</a>
            </li>
             <li>
              <a v-scroll-to.scrollTo="{ el: '#footer' }">Контакты</a>
            </li>
          </ul>
        </nav>
        <a v-scroll-to.scrollTo="{ el: '#contact' }" class="header--btn">
          <div class="btn--arrow">
            <svg width="19" height="10" viewBox="0 0 19 10" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M17.9419 5.44194C18.186 5.19786 18.186 4.80214 17.9419 4.55806L13.9645 0.580583C13.7204 0.336505 13.3247 0.336505 13.0806 0.580583C12.8365 0.82466 12.8365 1.22039 13.0806 1.46447L16.6161 5L13.0806 8.53553C12.8365 8.77961 12.8365 9.17534 13.0806 9.41942C13.3247 9.6635 13.7204 9.6635 13.9645 9.41942L17.9419 5.44194ZM0.5 5.625H17.5V4.375H0.5V5.625Z" fill="#F9FBFE"/>
            </svg>
          </div>
          Получить консультацию
        </a>
        <button class="burger--open" @click="openBurgerMenu">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
    </div>
  </header>
</template>

<script>
import VueScrollTo from 'vue-scrollto';
export default {
  name: "Header",
  directives : {
     scrollTo: VueScrollTo,
  },
  data() {
    return {
      Logo: "../public/img/Logo.svg"
    };
  },
  mounted() {
    const openBtn = document.querySelector(".burger--open");
    const closeBtn = document.querySelector(".close--modal");
    const burgerMenu = document.querySelector(".burger");
    const burgerLinks = document.querySelectorAll(".burger--main a");

    openBtn.addEventListener("click", () => {
      burgerMenu.style.top = "0";
      burgerMenu.style.transition = "top 0.3s ease";
      document.body.style.overflow = "hidden";
    });

    closeBtn.addEventListener("click", () => {
      burgerMenu.style.top = "-150vh";
      burgerMenu.style.transition = "top 0.3s ease";
      document.body.style.overflow = "auto";
    });

    burgerMenu.style.top = "-150vh";

    burgerLinks.forEach((link) => {
  link.addEventListener("click", () => {
    const burgerMenu = document.querySelector(".burger");
    burgerMenu.style.top = "-150vh";
    burgerMenu.style.transition = "top 0.3s ease";
    document.body.style.overflow = "auto";
  });
});
  },
};
</script>

<style scoped>
.header {
  width: 100%;
  position: absolute;
}
.burger {
  padding: 80px;
  position: absolute;
  z-index: 3;
  background: rgba(106, 153, 230, 0.02);
  backdrop-filter: blur(17.5px);
  height: 100vh;
  width: 100%;
}
.burger--inner {
    display: flex;
    flex-direction: column;
}
.burger--main {
  display: flex;
  flex-direction: column;
  gap: 80px;
  align-items: center;
  margin-top: 100px;
}
.burger--main a {
  font-style: normal;
  font-weight: 700;
  font-size: 32px;
  line-height: 39px;
  color: var(--white-);
}
.burger--header {
  display: flex;
  justify-content: flex-end;
}
.burger--btn {
    display: flex;
    align-items: center;
    flex-direction: column;
    font-style: normal;
    font-weight: 700;
    font-size: 32px;
    line-height: 39px;
    text-align: center;
    color: #F9FBFE;
    max-width: 271px;
}
.header--inner {
  margin-top: 90px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.burger--open {
  display: none;
  flex-direction: column;
  gap: 10px;
}
.burger--open span:nth-child(1) {
  border-radius: 2px;
  height: 2px;
  width: 16px;
  background-color: #FFFFFF;
}
.burger--open span:nth-child(2) {
    border-radius: 2px;
    height: 2px;
    width: 29px;
    background-color: #FFFFFF;
}
.burger--open span:nth-child(3) {
    border-radius: 2px;
    height: 2px;
    width: 16px;
    background-color: #FFFFFF;
}
.nav ul {
  display: flex;
  flex-direction: row;
  gap: 60px;
}
.nav ul li a {
  font-style: normal;
  font-weight: 400;
  font-size: 20px;
  line-height: 24px;
  color: var(--white-);
  position: relative;
  transition: transform 0.5s;
}

.nav ul li a::after {
    content: '';
    position: absolute;
    width: 130%;
    top: 30px;
    height: 2px;
    bottom: 0;
    left: 0;
    background-color: var(--blue-secondary-);
    transform: scaleX(0);
    transform-origin: bottom right;
    transition: transform 0.5s;
}
.nav ul li a:hover {
    color: #CDCDCD;
}
.nav ul li a:hover::after {
    transform-origin: bottom left;
    transform: scaleX(1);
}

.header--btn {
    display: flex;
    flex-direction: row;
    gap: 20px;
    justify-content: center;
    align-items: center;
    color: var(--white-);
}
.btn--arrow {
    width: 40px;
    height: 40px;
    background: var(--blue-secondary-);
    border-radius: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform 0.3s ease;
}

.header--btn:hover .btn--arrow {
    transform: translateX(10px);
}
.header--btn:hover {
  color: #CDCDCD;
}
@media screen and (max-width: 1200px) {
  .nav {
    display: none;
  }
  .header--btn {
    display: none;
  }
  .burger--open {
    display: flex;
  }
}
@media screen and (max-width: 530px) {
  .logo {
    max-width: 70%;
  }
}

</style>