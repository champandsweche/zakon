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
        { question: "Тут будет вопрос", answer: "а тут ответ", isOpen: false, isRotated: false },
        { question: "Тут будет вопрос", answer: "а тут ответ", isOpen: false, isRotated: false },
        { question: "Тут будет вопрос", answer: "а тут ответ", isOpen: false, isRotated: false },
        { question: "Тут будет вопрос", answer: "а тут ответ", isOpen: false, isRotated: false },
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
  }
}


</style>