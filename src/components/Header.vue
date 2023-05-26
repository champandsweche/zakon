<template>
    <header class="header">
        <div class="burger" :class="{ 'burger--active': isBurgerMenuOpen }">
            <div class="burger--inner">
                <div class="burger--header">
                    <button class="close--modal" @click="closeBurgerMenu">
                        <svg class="burger__svg" width="34" height="34" viewBox="0 0 34 34" fill="none"
                             xmlns="http://www.w3.org/2000/svg">
                            <path d="M29.7499 29.7499L4.25 4.25" stroke="white" stroke-width="2" stroke-linecap="round"
                                  stroke-linejoin="round"/>
                            <path d="M29.7501 4.25L4.25 29.7501" stroke="white" stroke-width="2" stroke-linecap="round"
                                  stroke-linejoin="round"/>
                        </svg>
                    </button>
                </div>
                <div class="burger--main">
                    <a v-scroll-to.scrollTo="{ el: '#services' }" @click="closeBurgerMenu">Услуги</a>
                    <a v-scroll-to.scrollTo="{ el: '#contact' }" class="burger--btn" @click="closeBurgerMenu">
                        <div class="btn--arrow">
                            <svg class="burger__svg" width="19" height="10" viewBox="0 0 19 10" fill="none"
                                 xmlns="http://www.w3.org/2000/svg">
                                <path d="M17.9419 5.44194C18.186 5.19786 18.186 4.80214 17.9419 4.55806L13.9645 0.580583C13.7204 0.336505 13.3247 0.336505 13.0806 0.580583C12.8365 0.82466 12.8365 1.22039 13.0806 1.46447L16.6161 5L13.0806 8.53553C12.8365 8.77961 12.8365 9.17534 13.0806 9.41942C13.3247 9.6635 13.7204 9.6635 13.9645 9.41942L17.9419 5.44194ZM0.5 5.625H17.5V4.375H0.5V5.625Z"
                                      fill="#F9FBFE"/>
                            </svg>
                        </div>
                        Получить консультацию
                    </a>
                    <a v-scroll-to.scrollTo="{ el: '#about' }" @click="closeBurgerMenu">О нас</a>
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
                        <li>
                            <a v-scroll-to.scrollTo="{ el: '#help' }">Помощь</a>
                        </li>
                    </ul>
                </nav>
                <a v-scroll-to.scrollTo="{ el: '#contact' }" class="header--btn">
                    <div class="btn--arrow">
                        <svg width="19" height="10" viewBox="0 0 19 10" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M17.9419 5.44194C18.186 5.19786 18.186 4.80214 17.9419 4.55806L13.9645 0.580583C13.7204 0.336505 13.3247 0.336505 13.0806 0.580583C12.8365 0.82466 12.8365 1.22039 13.0806 1.46447L16.6161 5L13.0806 8.53553C12.8365 8.77961 12.8365 9.17534 13.0806 9.41942C13.3247 9.6635 13.7204 9.6635 13.9645 9.41942L17.9419 5.44194ZM0.5 5.625H17.5V4.375H0.5V5.625Z"
                                  fill="#F9FBFE"/>
                        </svg>
                    </div>
                    Получить консультацию
                </a>
                <button class="burger-open" @click="toggleBurgerMenu">
                    <span class="burger-open__span"></span>
                    <span class="burger-open__span"></span>
                    <span class="burger-open__span"></span>
                </button>
            </div>
        </div>
    </header>
</template>

<script>
import VueScrollTo from 'vue-scrollto';

export default {
    name: "Header",
    directives: {
        scrollTo: VueScrollTo,
    },
    data() {
        return {
            Logo: "../public/img/Logo.svg",
            isBurgerMenuOpen: false
        };
    },
    methods: {
        toggleBurgerMenu() {
            this.isBurgerMenuOpen = !this.isBurgerMenuOpen;
            document.body.style.overflow = this.isBurgerMenuOpen ? "hidden" : "auto";
        },
        closeBurgerMenu() {
            this.isBurgerMenuOpen = false;
            document.body.style.overflowY = "scroll";
            this.scrollToSection();
        }
    },
    scrollToSection() {
        const selectedSection = document.querySelector("#selected-section");
        selectedSection.scrollIntoView({behavior: "smooth"});
    }
};
</script>

<style scoped>
.header {
    width: 100%;
    position: absolute;
}

.burger {
    padding: 80px 60px;
    position: absolute;
    z-index: 3;
    background: rgba(106, 153, 230, 0.02);
    backdrop-filter: blur(20px);
    height: 100vh;
    width: 100%;
    transition: transform .6s;
    transform: translateY(-200%);
}

.burger--active {
    transform: translateY(0);
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
    font-weight: 600;
    font-size: 32px;
    line-height: 1.3;
    color: var(--white-);
    transition: color .3s;
}

.burger--main a:hover {
    color: var(--blue-primary-);
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
    margin-top: 70px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
}

.burger-open {
    display: none;
    flex-direction: column;
    width: 30px;
    gap: 10px;
}

.burger-open__span {
    transition: background-color .3s, width .3s;
    background-color: var(--white-);
    display: block;
}

.burger-open:hover .burger-open__span {
    background-color: var(--blue-primary-);
    width: 100%;
}

.burger-open__span:nth-child(1) {
    border-radius: 2px;
    height: 2px;
    width: 16px;
    margin-left: auto;
}

.burger-open__span:nth-child(2) {
    border-radius: 2px;
    height: 2px;
    width: 29px;
    background-color: #FFFFFF;
}

.burger-open__span:nth-child(3) {
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

.burger__svg path {
    transition: stroke .3s;
}

.close--modal:hover .burger__svg path {
    stroke: var(--blue-primary-);
}

@media screen and (max-width: 1450px) {
    .nav {
        display: none;
    }

    .header--btn {
        display: none;
    }

    .burger-open {
        display: flex;
    }
}

@media (max-width: 1200px) {
    .burger--main a {
        font-size: 28px;
    }
}

@media (max-width: 992px) {
    .header--inner {
        margin-top: 50px;
    }
}

@media (max-width: 768px) {
    .burger {
        padding: 65px 40px;
    }

    .header--inner {
        margin-top: 40px;
    }

    .burger--main a {
        font-size: 26px;
    }
}

@media (max-width: 600px) {
    .burger--main a {
        font-size: 24px;
    }
}

@media (max-width: 468px) {
    .burger {
        padding: 50px 30px;
    }

    .burger--main a {
        font-size: 22px;
    }
}

@media screen and (max-width: 530px) {
    .logo {
        max-width: 70%;
    }
}

</style>