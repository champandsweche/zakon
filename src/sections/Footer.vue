npm<template>
    <div class="section--footer">
        <div class="container">
            <div class="footer--inner">
                <div class="left-side">
                    <img :src="Logo" alt="" class="logo">
                  <p>В современном мире, где правовые вопросы играют все более важную роль в нашей повседневной жизни, мы осознаем, что наличие квалифицированного юридического партнера может оказаться ключевым фактором успеха для частных лиц и предприятий. Наша команда состоит из опытных юристов, которые обладают глубокими знаниями и обширным опытом в различных областях права.</p>
                  <p>Кроме того, мы ценим время и ресурсы наших клиентов. Поэтому мы стараемся предоставить быстрое и эффективное решение ваших юридических проблем. Наша команда обладает не только глубокими знаниями в области права, но и стремится быть в курсе последних изменений в законодательстве и судебной практике. Мы используем передовые технологии и методы работы, чтобы обеспечить максимальную эффективность и удовлетворить все ваши потребности.</p>
                </div>
                <div class="right-side">
                    <div class="text">
                        <b>Контакты</b>
                        <p>Аристей - юридические услуги</p>
                    </div>
                    <div class="text">
                        <b>info@gerrart.ru</b>
                        <b>+7 (800) 775 02 13</b>
                        <p>г Белореченск, Шалимова 5/1</p>
                    </div>
                    <img :src="El" alt="">
                </div>
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
.footer--inner {
  gap: 100px;
}
.left-side p {
  color: var(--white-);
  line-height: 25px;
  text-indent: 25px;
}
.left-side img {
  max-width: 50%;
}
.right-side img{
  scale: .7;
}
.section--footer {
    margin-top: 365px;
    background-color: var(--dark-);
    padding-top: 168px;
    padding-bottom: 105px;
}
.footer--inner {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.left-side {
    display: flex;
    flex-direction: column;
    gap: 50px;
    max-width: 50%;
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
    color: var(--white-);
}

.btn {
    display: flex;
    flex-direction: row;
    gap: 20px;
    align-items: center;
    color: var(--white-);
    padding: 15px 20px;
    border: 1.25px solid var(--white-);
    border-radius: 100px;
    max-width: 250px;
    cursor: pointer;
}

.btn--arrow {
    width: 40px;
    height: 40px;
    background: var(--white-);
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
    color: var(--white-);
}

.text p {
    font-style: normal;
    font-weight: 400;
    font-size: 24px;
    line-height: 29px;
    display: flex;
    align-items: center;
    color: var(--white-);
    opacity: 0.5;
}

@media screen and (max-width: 1200px) {
    .footer--inner {
        display: flex;
        flex-direction: column;
        gap: 100px;
    }
  .left-side {
    max-width: 100%;
  }
  .right-side {
    max-width: 100%;
  }
    .left-side img{
      max-width: 100%;
    }
    .right-side img{
      max-width: 50%;
    }
    .left-side p {
      font-size: 16px;
      line-height: 25px;
    }
}
@media screen and (max-width: 480px) {
  .right-side .text b{
    font-size: 34px;
  }
  .right-side .text p {
    font-size: 20px;
  }
  .right-side img {
    display: none;
  }
}
</style>