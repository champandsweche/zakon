<template>
  <div class="section--service">
    <div class="container">
      <div class="section--service--inner">
        <div class="inner--header">
          <div class="left-side">
            <b>01</b>
            <div class="title">
              <p>Услуги и цены</p>
              <div class="progress-bar">
                <span></span>
                <span></span>
              </div>
            </div>
          </div>
          <div class="right--side">
            <button class="slider--btn prev reviews__button--prev" type="button" @click="moveSlider('prev')">
              <svg width="73" height="15" viewBox="0 0 73 15" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M1.07864 6.79289C0.688113 7.18341 0.688113 7.81658 1.07864 8.2071L7.4426 14.5711C7.83312 14.9616 8.46629 14.9616 8.85681 14.5711C9.24734 14.1805 9.24734 13.5474 8.85681 13.1568L3.19996 7.49999L8.85681 1.84314C9.24734 1.45262 9.24734 0.819451 8.85681 0.428927C8.46629 0.0384023 7.83312 0.0384022 7.4426 0.428926L1.07864 6.79289ZM72.8757 6.5L1.78574 6.49999L1.78574 8.49999L72.8757 8.5L72.8757 6.5Z"
                    fill="#1F1F1F"/>
              </svg>
            </button>
            <button class="slider--btn next reviews__button--next" type="button" @click="moveSlider('next')">
              <svg width="73" height="15" viewBox="0 0 73 15" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M72.707 8.20711C73.0975 7.81658 73.0975 7.18342 72.707 6.79289L66.343 0.428932C65.9525 0.0384078 65.3194 0.0384078 64.9288 0.428932C64.5383 0.819457 64.5383 1.45262 64.9288 1.84315L70.5857 7.5L64.9288 13.1569C64.5383 13.5474 64.5383 14.1805 64.9288 14.5711C65.3194 14.9616 65.9525 14.9616 66.343 14.5711L72.707 8.20711ZM0.909912 8.5H71.9999V6.5H0.909912V8.5Z"
                    fill="#1F1F1F"/>
              </svg>
            </button>
          </div>
        </div>
        <div class="inner--main">
          <swiper class="service-swiper"
                  :breakpoints="swiperOptions.breakpoints"
                  :pagination="swiperOptions.pagination"
                  :navigation="swiperOptions.navigation"
          >
            <swiper-slide class="swiper-slide card" v-for="(card, index) in cards" :key="index">
              <b class="card-id">#{{ card.id }}</b>
              <img :src="card.image" alt="Картинка">
              <h3 class="card-title">{{ card.title }}</h3>
              <p class="card-description">{{ card.description }}</p>
              <div class="card-price">
                <span></span>
                <p>От {{ card.price }} за услугу</p>
              </div>
              <a v-scroll-to.scrollTo="{ el: '#contact' }" class="card-btn">
                <div class="card-btn--arrow">
                  <svg width="19" height="10" viewBox="0 0 19 10" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                        d="M17.9419 5.44194C18.186 5.19786 18.186 4.80214 17.9419 4.55806L13.9645 0.580583C13.7204 0.336505 13.3247 0.336505 13.0806 0.580583C12.8365 0.82466 12.8365 1.22039 13.0806 1.46447L16.6161 5L13.0806 8.53553C12.8365 8.77961 12.8365 9.17534 13.0806 9.41942C13.3247 9.6635 13.7204 9.6635 13.9645 9.41942L17.9419 5.44194ZM0.5 5.625H17.5V4.375H0.5V5.625Z"
                        fill="#F9FBFE"/>
                  </svg>
                </div>
                Записаться
              </a>
            </swiper-slide>
          </swiper>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {Swiper, SwiperSlide} from "swiper/vue";
import SwiperCore, {Navigation} from "swiper";

SwiperCore.use([Navigation]);
import 'swiper/swiper-bundle.css';
import VueScrollTo from "vue-scrollto";


export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  directives : {
     scrollTo: VueScrollTo,
  },
  data() {
    return {
      cards: [
        {
          id: 1,
          title: 'Административное право',
          description: 'Наши опытные юристы готовы предоставить консультации и экспертную помощь в различных сферах, связанных с административными правомочиями, административными установлениями и процедурами, соответствующими законодательству по административным правонарушениям.',
          image: '../public/img/sectionService/административное_право_img.svg',
          price: '1500',
        },
        {
          id: 2,
          title: 'Трудовое право',
          description: 'Трудовое право - это область права, регулирующая отношения между работниками и работодателями. Она включает в себя нормы, которые определяют условия труда, права и обязанности сторон трудового договора, порядок заключения и расторжения трудовых договоров, гарантии и компенсации работникам при увольнении, заработную плату, социальные гарантии и другие аспекты, связанные с трудовыми отношениями.',
          image: '../public/img/sectionService/трудовое_право_img.svg',
          price: '2000',
        },
        {
          id: 3,
          title: 'Семейное право',
          description: 'Семейное право - это область права, которая регулирует отношения между членами семьи. Она включает в себя такие темы, как брак, развод, усыновление, опека над детьми, алименты, наследство и другие.',
          image: '../public/img/sectionService/семейное_право_img.svg',
          price: '200',
        },
        {
          id: 4,
          title: 'Банкротство и кредиты',
          description: 'Наша команда опытных юристов готова оказать квалифицированную помощь в области банкротства для физических и юридических лиц, включая консультации, помощь в организации банкротства, расчет долгов и погашение, представительство в суде по делам о банкротстве, оспаривание действий банкротных управляющих и многое другое.',
          image: '../public/img/sectionService/административное_право_img.svg',
          price: '5000',
        },
        {
          id: 5,
          title: ' Автомобильное право',
          description: 'Мы предлагаем услуги по оказанию помощи в случае ДТП, а также помощь в получении страховых выплат и возмещении ущерба. Наши опытные юристы помогут клиентам в вопросах, связанных с правами и обязанностями участников ДТП, оформлением документов, а также с представительством интересов клиента в суде.',
          image: '../public/img/sectionService/автомобильное_право_img.svg',
          price: '1000',
        },
          {
          id: 6,
          title: 'Земельное право',
          description: 'Наши юристы имеют обширный опыт в области земельного права и готовы предоставить экспертную помощь нашим клиентам во всех вопросах, связанных с земельными правами. Мы поможем вам выбрать наилучшие стратегии и подходы для решения сложных споров, связанных с земельными участками и предоставим консультации и помощь в оформлении всех необходимых документов по земельным правоотношениям.',
          image: '../public/img/sectionService/земельное_право_img.svg',
          price: '3500',
        },
      ],
      swiperOptions: {
        breakpoints: {
          1000: {
            slidesPerView: 1,
            spaceBetween: 40
          },
          1200: {
            slidesPerView: 2,
            spaceBetween: 40
          },
          1540: {
            slidesPerView: 3,
            spaceBetween: 30
          }
        },
        navigation: {
          nextEl: '.reviews__button--next',
          prevEl: '.reviews__button--prev'
        },
        pagination: {
          el: '.swiper-pagination',
          clickable: true
        }
      },
      modules: [Navigation]
    };
  }
};
</script>

<style scoped>
@import 'swiper/swiper-bundle.css';

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

.right--side {
  display: flex;
  gap: 27px;
}

.inner--main {
  overflow: hidden;
  margin-top: 120px;
}

.slider {
  display: flex;
  gap: 60px;
  transition: transform 0.5s ease-in-out;
  flex-wrap: nowrap;
}

.card {
  background: linear-gradient(271.42deg, #F2F7FF 23.59%, rgba(255, 255, 255, 0) 89.56%);
  border-radius: 25px;
  padding: 20px;
  height: 860px;
}

.card-id {
  font-style: normal;
  font-weight: 500;
  font-size: 50px;
  line-height: 61px;
  color: var(--blue-primary-);
}
.card img {
  margin-top: 25px;
}

.card-title {
  font-style: normal;
  font-weight: 500;
  font-size: 24px;
  line-height: 29px;
  color: var(--dark-);
  margin-top: 25px;
}

.card-description {
  font-style: normal;
  font-weight: 400;
  font-size: 17px;
  line-height: 21px;
  color: var(--dark-);
  margin-top: 30px;
  height: 252px;
}

.card-price {
  margin-top: 50px;
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

.card-price span {
  width: 16px;
  height: 16px;
  border-radius: 50px;
  background: var(--blue-primary-);
}

.card-price p {
  font-style: normal;
  font-weight: 500;
  font-size: 24px;
  line-height: 29px;
  color: var(--blue-primary-);
}

.slider--track {
  display: flex;
  flex-direction: row;
  gap: 60px;
}

.card-btn {
  margin-top: 50px;
  display: flex;
  flex-direction: row;
  gap: 20px;
  align-items: center;
  color: var(--dark-);
  padding: 15px 20px;
  border: 1.25px solid var(--dark-);
  border-radius: 100px;
  max-width: 316px;
}

.card-btn--arrow {
  width: 40px;
  height: 40px;
  background: var(--blue-primary-);
  border-radius: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.3s ease;
}

.card-btn:hover .card-btn--arrow {
  transform: translateX(10px);
}

.card-btn:hover {
  color: #CDCDCD;
}
@media screen and (max-width: 1200px) {
  .title p {
    font-size: 32px;
  }
}
@media screen and (max-width: 800px) {
  .inner--header {
    gap: 60px;
    flex-direction: column;
    align-items: flex-start;
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
