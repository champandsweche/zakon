<template>
  <div class="section--help">
    <div class="container">
      <div class="help--inner">
        <div class="left-side">
          <b>04</b>
          <div class="title">
            <h2>Помощь</h2>
            <div class="progress-bar">
              <span></span>
              <span></span>
            </div>
          </div>
        </div>
        <div class="description">
          <p>Здесь представлены ответы на самые часто задаваемые вопросы</p>
        </div>
        <div class="accordion">
          <div v-for="(item, index) in accordionItems" :key="index" class="accordion--item">
            <div class="accordion--header" @click="toggleAccordion(index)" :class="{ open: item.isOpen }">
              <p>{{ item.question }}</p>
              <AccordionIcon :isOpen="item.isOpen" :class="{ rotated: item.isRotated, returning: !item.isOpen && item.isRotated }" />
            </div>
            <div class="accordion--content" v-show="item.isOpen">
              <p>{{ item.answer }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import AccordionIcon from "@/icons/AccordionIcon.vue";

export default {
  name: "SectionHelp",
  components: { AccordionIcon },
  data() {
    return {
      accordionItems: [
        { question: "Какие документы мне необходимы для регистрации фирмы?", answer: "Для регистрации фирмы обычно требуется следующий набор документов: копия паспорта учредителей, устав компании, документы, подтверждающие адрес регистрации компании, а также заполненные и подписанные регистрационные формы. Однако, требования могут различаться в зависимости от юрисдикции, в которой вы планируете зарегистрировать фирму. Рекомендуется обратиться к юристу или специалисту по регистрации компаний для получения точной информации.", isOpen: false, isRotated: false },
        { question: "Какой срок рассмотрения моего дела в суде?", answer: "Сроки рассмотрения дел в суде могут значительно различаться в зависимости от типа дела, сложности ситуации, нагрузки на суд и других факторов. Обычно судебные процессы занимают несколько месяцев, однако некоторые сложные дела могут растянуться на годы. Важно помнить, что каждое дело уникально, и конкретный срок рассмотрения будет определяться судом в процессе его рассмотрения.", isOpen: false, isRotated: false },
        { question: "Какие требования необходимо соблюсти при покупке недвижимости?", answer: "При покупке недвижимости необходимо учитывать следующие требования: провести юридическую проверку объекта недвижимости, составить и подписать договор купли-продажи, зарегистрировать сделку в соответствующем реестре недвижимости, уплатить соответствующие налоги и сборы, а также соблюдать все требования, установленные законодательством вашей страны или региона.", isOpen: false, isRotated: false },
        { question: "Каковы последствия нарушения авторских прав?", answer: "Нарушение авторских прав может иметь серьезные последствия. Автор или правообладатель имеет право на защиту своих прав путем обращения в суд и требования компенсации за ущерб, причиненный нарушением. В случае признания нарушения, нарушитель может быть обязан выплатить штраф, возместить убытки и прекратить использование нарушающего материала.", isOpen: false, isRotated: false },
      ]
    };
  },
  methods: {
    toggleAccordion(index) {
      this.accordionItems.forEach((item, i) => {
        if (i === index) {
          item.isOpen = !item.isOpen;
          item.isRotated = !item.isRotated;
        } else {
          item.isOpen = false;
          item.isRotated = item.isOpen;
        }
      });
    }
  }
};
</script>

<style scoped>

.help--inner {
  display: flex;
  flex-direction: column;
  gap: 70px;
}

.section--help {
  margin-top: 365px;
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

.title h2 {
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
.description p {
  max-width: 1000px;
  font-style: normal;
  font-weight: 700;
  font-size: 40px;
  line-height: 49px;
  color: var(--blue-secondary-);
}
.accordion {
  display: flex;
  flex-direction: column;
  gap: 40px;
}
.accordion--header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid var(--blue-secondary-);
  padding: 20px 0px;
  cursor: pointer;

}
.accordion--header p {
  font-style: normal;
  font-weight: 500;
  font-size: 30px;
  line-height: 37px;
  color: var(--dark-);
}
.accordion--content{
  margin-top: 40px;
  transition: transform 0.5s ease;
}
.accordion--content p{
  font-style: normal;
  font-weight: 500;
  font-size: 25px;
  line-height: 30px;
}
.rotated {
  transition: transform 0.5s ease;
  transform: rotate(495deg);
}
.returning {
  transition: transform 0.5s ease;
  transform: rotate(0deg);
}
.accordion--header.open {
  border-color: var(--blue-primary-);
}
.accordion--header.open p{
  color: var(--blue-primary-);
}
@media screen and (max-width: 400px) {
  .left-side {
    flex-direction: column;
    align-items: flex-start;
  }
  .left-side b {
    text-align: center;
    width: 100%;
  }
}
</style>