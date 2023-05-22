<template>
    <div class="section--about">
        <div class="container">
            <div class="section--about--inner">
                <div class="inner--header">
                    <div class="left-side">
                        <b>02</b>
                        <div class="title">
                            <p>Правовая поддержка</p>
                            <div class="progress-bar">
                                <span></span>
                                <span></span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="inner--main">
                    <div class="main--left-side">
                        <img :src="vector" alt="Декоративный элемент">
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
.inner--header {
    margin-top: 360px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.left-side {
    display: flex;
    align-items: center;
    gap: 60px;
}

.left-side b {
    font-style: normal;
    font-weight: 700;
    font-size: 96px;
    line-height: 117px;
    color: var(--blue-primary-);
}

.title {
    display: flex;
    flex-direction: column;
    gap: 25px;
}

.title p {
    font-style: normal;
    font-weight: 500;
    font-size: 40px;
    line-height: 49px;
    color: var(--dark-);
}

.progress-bar {
    display: flex;
    align-items: center;
}

.progress-bar span:nth-child(1) {
    position: relative;
    width: 16px;
    height: 16px;
    border-radius: 200px;
    background-color: var(--blue-primary-);
}

.progress-bar span:nth-child(2) {
    width: 70%;
    max-width: 200px;
    height: 3px;
    background-color: var(--blue-primary-);
}

.inner--main {
    margin-top: 120px;
    display: flex;
    flex-direction: row;
    gap: 120px;
}

.main--left-side {
    width: 100%;
}

.main--right-side {
    display: flex;
    flex-direction: column;
    gap: 60px;
}

.main--right-side b {
    font-style: normal;
    font-weight: 700;
    font-size: 32px;
    line-height: 39px;
    display: flex;
    align-items: center;
    font-feature-settings: 'kern' off;
    color: var(--blue-secondary-);
}

.main--right-side p {
    font-family: 'Montserrat', sans-serif;
    font-weight: 400;
    font-size: 24px;
    line-height: 29px;
    color: var(--dark-);
    opacity: 0.75;

}

@media screen and (max-width: 1200px) {
    .title p {
        font-size: 32px;
    }
}

@media screen and (max-width: 1000px) {
    .inner--main {
        flex-direction: column;
    }

    .main--left-side {
        display: flex;
        justify-content: center;
    }
}

@media screen and (max-width: 500px) {
    .inner--header {
        gap: 40px;
        flex-direction: column;
        align-items: center;
    }

    .left-side {
        display: flex;
        flex-direction: column;
    }

    .right--side {
        display: none;
    }
}

</style>