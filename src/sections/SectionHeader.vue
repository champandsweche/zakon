<template>
  <div class="section--header">
    <div class="container">
      <div class="section--header--inner">
        <div class="left--side">
          <b>Экспертные юридические решения для вашего бизнеса</b>
          <p>Мы оказываем профессиональную помощь нашим клиентам в решении любых проблем, связанных с банкротством или
            кредитами.</p>
          <a v-scroll-to.scrollTo="{ el: '#contact' }" class="btn">
            <div class="btn--arrow">
              <svg width="19" height="10" viewBox="0 0 19 10" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M17.9419 5.44194C18.186 5.19786 18.186 4.80214 17.9419 4.55806L13.9645 0.580583C13.7204 0.336505 13.3247 0.336505 13.0806 0.580583C12.8365 0.82466 12.8365 1.22039 13.0806 1.46447L16.6161 5L13.0806 8.53553C12.8365 8.77961 12.8365 9.17534 13.0806 9.41942C13.3247 9.6635 13.7204 9.6635 13.9645 9.41942L17.9419 5.44194ZM0.5 5.625H17.5V4.375H0.5V5.625Z"
                    fill="#F9FBFE"/>
              </svg>
            </div>
            Получить консультацию
          </a>
        </div>
        <div class="right--side">
          <div class="section-header__left">
            <a v-scroll-to.scrollTo="{ el: '#services' }" class="item1 item">
              <b>01</b>
              <p>Услуги и цены</p>
            </a>
            <a v-scroll-to.scrollTo="{ el: '#about' }" class="item2 item">
              <b>02</b>
              <p>Правовая поддержка</p>
            </a>
          </div>
          <div class="section-header__right">
            <a v-scroll-to.scrollTo="{ el: '#contact' }" class="item3 item">
              <b>03</b>
              <p>Заявка на консультацию</p>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import VueScrollTo from 'vue-scrollto';
export default {
  name: "SectionHeader",
  directives : {
     scrollTo: VueScrollTo,
  },
  data() {
    return {
      bg: "../public/img/sectionHeader/bg.png"
    };
  }
}
</script>
<style scoped>
.section--header {
  background-image: url("../../public/img/sectionHeader/bg.png");
  width: 100%;
  height: 1246px;
  border-radius: 0px 0px 0px 250px;
  padding-top: 326px;
  display: flex;
  flex-direction: row;
  padding-bottom: 84px;
}

.section--header--inner {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 60px;
}

.left--side {
  max-width: 825px;
  display: flex;
  flex-direction: column;
  gap: 80px;
}

.left--side b {
  font-style: normal;
  font-weight: 700;
  font-size: 64px;
  line-height: 78px;
  color: var(--white-);
}

.left--side p {
  font-style: normal;
  font-weight: 300;
  font-size: 24px;
  line-height: 130%;
  color: var(--white-);
  max-width: 750px;
}

.btn {
  display: flex;
  flex-direction: row;
  gap: 20px;
  align-items: center;
  color: var(--white-);
  padding: 15px 20px;
  border: 1.25px solid #1D48BB;
  border-radius: 100px;
  max-width: 316px;
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

.btn:hover .btn--arrow {
  transform: translateX(10px);
}

.btn:hover {
  color: #CDCDCD;
}

.right--side {
  display: flex;
  align-items: center;
}

.item {
  cursor: pointer;
  transition: transform 0.3s ease;
  width: 15vw;
  height: 15vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 100px;
  gap: 21px;
  border: 1px solid #6A99E6;
  border-radius: 2000px;
}

.item:hover {
  border-width: 0;
  background-color: var(--dark-);
  transform: translateY(15px);
}

.item b {
  font-style: normal;
  font-weight: 700;
  font-size: 24px;
  line-height: 29px;
  color: var(--white-);
}

.item p {
  font-style: normal;
  font-weight: 300;
  font-size: 20px;
  line-height: 29px;
  text-align: center;
  color: var(--white-);
  max-width: 186px;
}

.item1 {
  margin-bottom: 30px;
}

.item2 {
  margin-left: 10px;
}
@media screen and (max-width: 1700px) {
.section--header {
    height: 1100px;
    padding-top: 230px;
}
}
@media screen and (max-width: 1200px) {
.section--header--inner {
    flex-direction: column;
}
  .left--side {
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  .right--side{
    flex-direction: row;
    align-items: center;
    gap: 10px;
  }
  .section-header__left {
    display: flex;
    flex-direction: row;
    align-items: center;
  }
  .item1 {
    margin: 0;
  }
  .section--header {
    border-radius: 0;
}
}
@media screen and (max-width: 950px) {
    .left--side {
      gap: 40px;
    }
  .item p {
  font-size: 16px;
}
}
@media screen and (max-width: 800px) {
    .left--side b{
      font-size: 35px;
      line-height: 120%;
    }
}
@media screen and (max-width: 695px) {
  .right--side {
    flex-direction: column-reverse;
    gap: 0;
  }
  .item1 {
    position: relative;
  }
    .item3 {
    position: relative;
      margin-bottom: -50px;
  }
    .item2 {
      margin: 0;
    }
    .item {
      padding: 80px;
      gap: 0;
    }
    .item p{
      line-height: 130%;
    }
}
@media screen and (max-width: 470px) {
  .left--side b{
      font-size: 25px;
      line-height: 120%;
    }
  .item p{
    font-size: 13px;
      line-height: 120%;
    }
}

</style>