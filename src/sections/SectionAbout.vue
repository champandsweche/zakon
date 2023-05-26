<template>
    <div class="section--about inner--header">
        <div class="container">
            <div class="section--about--inner">
                <div class="title">
                    <span class="title__number">02</span>
                    <div class="title__content">
                        <p>Правовая поддержка</p>
                        <div class="title__progress">
                            <span></span>
                            <span></span>
                        </div>
                    </div>
                </div>
                <div class="inner--main">
                    <div class="main--left-side">
                        <img :src="vector" alt="Декоративный элемент" width="330" height="330">
                    </div>
                    <div class="main--right-side">
                        <b>Мы понимаем, что в современном быстро меняющемся мире, правовые вопросы могут стать серьезным
                            препятствием для развития вашего бизнеса.</b>
                        <p>Поэтому наша задача – помочь вам минимизировать риски и достичь успеха, предлагая комплексный
                            набор юридических услуг, адаптированных под ваши потребности.</p>
                        <a v-scroll-to.scrollTo="{ el: '#contact' }" class="btn">
                            <div class="btn--arrow">
                                <svg width="19" height="10" viewBox="0 0 19 10" fill="none"
                                     xmlns="http://www.w3.org/2000/svg">
                                    <path d="M17.9419 5.44194C18.186 5.19786 18.186 4.80214 17.9419 4.55806L13.9645 0.580583C13.7204 0.336505 13.3247 0.336505 13.0806 0.580583C12.8365 0.82466 12.8365 1.22039 13.0806 1.46447L16.6161 5L13.0806 8.53553C12.8365 8.77961 12.8365 9.17534 13.0806 9.41942C13.3247 9.6635 13.7204 9.6635 13.9645 9.41942L17.9419 5.44194ZM0.5 5.625H17.5V4.375H0.5V5.625Z"
                                          fill="#F9FBFE"/>
                                </svg>
                            </div>
                            Заполнить заявку
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import VueScrollTo from "vue-scrollto";

export default {
    name: "SectionAbout",
    directives: {
        scrollTo: VueScrollTo,
    },
    data() {
        return {
            vector: "../public/img/sectionAbout/Vector.svg"
        };
    }
}
</script>

<style scoped>
.inner--main {
    margin-top: 120px;
    display: flex;
    gap: 120px;
}

.main--left-side {
    max-width: 330px;
    width: 100%;
}

.main--right-side {
    max-width: 1000px;
    width: 100%;
    display: flex;
    flex-direction: column;
}

.main--right-side b {
    font-style: normal;
    font-weight: 700;
    font-size: 32px;
    line-height: 1.2;
    display: flex;
    align-items: center;
    font-feature-settings: 'kern' off;
    margin-bottom: 50px;
    color: var(--blue-secondary-);
}

.main--right-side p {
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
    font-size: 24px;
    color: var(--dark-);
    opacity: 0.75;
    margin-bottom: 75px;
}

@media screen and (max-width: 1400px) {
    .inner--main {
        gap: 60px;
    }

    .main--right-side b {
        font-size: 26px;
    }

    .main--right-side p {
        font-size: 20px;
        margin-bottom: 40px;
    }

    .main--left-side img {
        width: 290px;
        height: 290px;
    }
}

@media (max-width: 1200px) {
    .inner--main {
        margin-top: 90px;
    }

    .main--right-side b {
        font-size: 24px;
        margin-bottom: 30px;
    }

    .main--right-side p {
        font-size: 18px;
        margin-bottom: 40px;
    }
}

@media screen and (max-width: 992px) {
    .inner--main {
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    .main--right-side .btn,
    .main--left-side img {
        margin: 0 auto;
    }
}

@media (max-width: 768px) {
    .inner--main {
        margin-top: 70px;
        gap: 45px;
    }

    .main--right-side b {
        font-size: 22px;
        margin-bottom: 30px;
    }

    .main--right-side p {
        font-size: 18px;
    }

    .main--left-side img {
        width: 250px;
        height: 250px;
    }
}

@media (max-width: 600px) {
    .inner--main {
        gap: 35px;
    }

    .main--right-side b {
        font-size: 20px;
        margin-bottom: 30px;
    }

    .main--right-side p {
        font-size: 16px;
    }

    .main--left-side img {
        width: 220px;
        height: 220px;
    }
}

@media screen and (max-width: 468px) {
    .main--right-side b {
        font-size: 18px;
        margin-bottom: 30px;
    }

    .main--left-side img {
        width: 190px;
        height: 190px;
    }
}

</style>