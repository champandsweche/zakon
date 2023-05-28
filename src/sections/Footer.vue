<template>
  <div class="section--footer">
    <div class="container">
      <div class="footer--inner">
        <div class="left-side">
          <img :src="Logo" alt="" class="logo">
          <div class="left-side__content">
            <div class="footer__info-list">
              <span class="footer__info-span">ИНН - 2368016435</span>
              <span class="footer__info-span">ОРГН - 1222300020865</span>
            </div>
            <span class="footer__list-title">Категории услуг:</span>
            <ul class="footer__list">
              <li class="footer__item">Юридическое право</li>
              <li class="footer__item">Семейное право</li>
              <li class="footer__item">Административное право</li>
              <li class="footer__item">Автомобильное право</li>
              <li class="footer__item">Земельное право</li>
              <li class="footer__item">Банкротство и кредиты</li>
            </ul>
          </div>
        </div>
        <div class="right-side">
          <div class="text">
            <b>Контакты</b>
            <p>Аристей - юридические услуги</p>
          </div>
          <div class="text">
            <b>zakon@aristei24.ru</b>
            <b>+7 (800) 775 02 13</b>
            <p>г Белореченск, Шалимова 5/1</p>
          </div>
          <div class="text">
            <b>График работы:</b>
            <p>ПН-ПТ - с 8:00 до 19:00</p>
            <p>СБ - с 10:00 до 15:00</p>
          </div>
        </div>
      </div>
    </div>
    <div class="copyright">
      <div class="container">
        <p>© Все права защищены ООО “Гераарт” 2023 </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      Logo: "../public/img/Logo.svg",
      El: "../public/img/Footer/el.svg"
    };
  },
}
</script>

<style scoped>
.section--footer {
  margin-top: 265px;
  background-color: var(--dark-);
  padding-top: 168px;
}

.footer--inner {
  gap: 100px;
  color: var(--white-);
  margin-bottom: 168px;
}

.left-side p {
  line-height: 25px;
  text-indent: 25px;
}

.right-side img {
  scale: .7;
}

.footer--inner {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.left-side {
  display: flex;
  flex-direction: column;
  max-width: 50%;
}

.left-side__content {
  margin-top: 60px;
}

.footer__info-list {
  margin-bottom: 60px;
}

.footer__info-span,
.footer__list-title {
  display: block;
  font-size: 28px;
}

.footer__info-span:not(:last-child) {
  margin-bottom: 25px;
}

.footer__list-title {
  margin-bottom: 25px;
}

.footer__list {
  display: flex;
  flex-direction: column;
  gap: 15px;
  color: rgba(255, 255, 255, 0.6);
  font-size: 18px;
}

.left-side form {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.left-side form input {
  align-items: center;
  padding: 25px;
  gap: 10px;
  width: 100%;
  max-width: 450px;
  background: var(--white-);
  border-radius: 25px;
  border: 1px solid var(--white-);
}

.left-side p {
  font-size: 22px;
  line-height: 35px;
}

.left-side b {
  font-style: normal;
  font-weight: 700;
  font-size: 40px;
  line-height: 49px;
  display: flex;
  align-items: center;
}

.right-side {
  display: flex;
  flex-direction: column;
  gap: 60px;
}

.text {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.text b {
  font-style: normal;
  font-weight: 700;
  font-size: 40px;
  line-height: 130%;
}

.text p {
  font-style: normal;
  font-weight: 400;
  font-size: 24px;
  line-height: 29px;
  display: flex;
  align-items: center;
  opacity: 0.5;
}

.copyright {
  background-color: #111111;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 40px 0;
}

.copyright p {
  color: var(--white-);
  font-size: 20px;
  line-height: 1.3;
  text-align: center;
}

@media screen and (max-width: 1200px) {
  .section--footer {
    padding-top: 100px;
    margin-top: 180px;
    text-align: center;
  }

  .footer--inner {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 70px;
    margin-bottom: 100px;
  }

  .left-side {
    max-width: 100%;
  }

  .right-side {
    gap: 50px;
  }

  .left-side img {
    margin: 0 auto;
  }

  .left-side p {
    font-size: 16px;
    line-height: 25px;
  }

  .text {
    align-items: center;
    gap: 15px;
  }

  .text b {
    font-size: 36px;
  }

  .text p {
    font-size: 22px;
  }

  .footer__info-span,
  .footer__list-title {
    font-size: 26px;
  }

  .right-side img {
    scale: 1;
    margin: 0 auto;
  }
}

@media (max-width: 992px) {
  .footer--inner {
    gap: 50px;
  }

  .text b {
    font-size: 32px;
  }

  .text p {
    font-size: 20px;
  }

  .left-side__content {
    margin-top: 50px;
  }

  .footer__info-span,
  .footer__list-title {
    font-size: 24px;
  }

  .footer__info-list {
    margin-bottom: 45px;
  }

  .footer__info-span:not(:last-child) {
    margin-bottom: 15px;
  }
}

@media (max-width: 768px) {
  .section--footer {
    padding-top: 70px;
    margin-top: 100px;
  }

  .footer--inner {
    margin-bottom: 70px;
  }

  .footer__info-span,
  .footer__list-title {
    font-size: 22px;
  }

  .text b {
    font-size: 28px;
  }

  .text p {
    font-size: 18px;
  }

  .copyright p {
    font-size: 18px;
  }
}

@media (max-width: 600px) {
  .section--footer {
    padding-top: 60px;
    margin-top: 70px;
  }

  .footer--inner {
    margin-bottom: 60px;
  }

  .footer__info-span,
  .footer__list-title {
    font-size: 20px;
  }

  .text b {
    font-size: 26px;
  }

  .text p {
    font-size: 16px;
  }

  .copyright {
    padding: 30px 0;
  }

  .copyright p {
    font-size: 16px;
  }

  .right-side img {
    width: 250px;
    height: 270px;
  }

  .copyright p {
    font-size: 16px;
  }
}

@media screen and (max-width: 480px) {
  .section--footer {
    padding-top: 50px;
  }

  .footer--inner {
    margin-bottom: 50px;
  }

  .footer--inner {
    gap: 40px;
  }

  .footer__info-span,
  .footer__list-title {
    font-size: 18px;
  }

  .footer__list {
    font-size: 16px;
  }

  .text b {
    font-size: 22px;
  }

  .copyright p {
    font-size: 14px;
  }
}
</style>