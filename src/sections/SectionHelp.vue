<template>
    <div class="section--help">
        <div class="container">
            <div class="help--inner inner--header">
                <div class="title">
                    <span class="title__number">04</span>
                    <div class="title__content">
                        <p>Помощь</p>
                        <div class="title__progress">
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
                            <AccordionIcon :isOpen="item.isOpen"
                                           :class="{ rotated: item.isRotated, returning: !item.isOpen && item.isRotated }"/>
                        </div>
                        <div class="accordion--content" :class="{ 'accordion--content--open': item.isOpen }">
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
    components: {AccordionIcon},
    data() {
        return {
            accordionItems: [
                {
                    question: "Какие документы мне необходимы для регистрации фирмы?",
                    answer: "Для регистрации фирмы обычно требуется следующий набор документов: копия паспорта учредителей, устав компании, документы, подтверждающие адрес регистрации компании, а также заполненные и подписанные регистрационные формы. Однако, требования могут различаться в зависимости от юрисдикции, в которой вы планируете зарегистрировать фирму. Рекомендуется обратиться к юристу или специалисту по регистрации компаний для получения точной информации.",
                    isOpen: false,
                    isRotated: false
                },
                {
                    question: "Какой срок рассмотрения моего дела в суде?",
                    answer: "Сроки рассмотрения дел в суде могут значительно различаться в зависимости от типа дела, сложности ситуации, нагрузки на суд и других факторов. Обычно судебные процессы занимают несколько месяцев, однако некоторые сложные дела могут растянуться на годы. Важно помнить, что каждое дело уникально, и конкретный срок рассмотрения будет определяться судом в процессе его рассмотрения.",
                    isOpen: false,
                    isRotated: false
                },
                {
                    question: "Какие требования необходимо соблюсти при покупке недвижимости?",
                    answer: "При покупке недвижимости необходимо учитывать следующие требования: провести юридическую проверку объекта недвижимости, составить и подписать договор купли-продажи, зарегистрировать сделку в соответствующем реестре недвижимости, уплатить соответствующие налоги и сборы, а также соблюдать все требования, установленные законодательством вашей страны или региона.",
                    isOpen: false,
                    isRotated: false
                },
                {
                    question: "Каковы последствия нарушения авторских прав?",
                    answer: "Нарушение авторских прав может иметь серьезные последствия. Автор или правообладатель имеет право на защиту своих прав путем обращения в суд и требования компенсации за ущерб, причиненный нарушением. В случае признания нарушения, нарушитель может быть обязан выплатить штраф, возместить убытки и прекратить использование нарушающего материала.",
                    isOpen: false,
                    isRotated: false
                },
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
        },
    },
};
</script>

<style scoped>

.help--inner {
    display: flex;
    flex-direction: column;
    gap: 70px;
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
    padding: 20px 0;
    cursor: pointer;

}

.accordion--header p {
    font-style: normal;
    font-weight: 500;
    font-size: 26px;
    line-height: 1.4;
    color: var(--dark-);
    transition: color .3s;
}

.accordion--header p:hover {
    color: var(--blue-primary-);
}

.accordion--content {
    margin-top: 40px;
    overflow: hidden;
    transition: max-height 0.3s;
    max-height: 0;
}

.accordion--content--open {
    max-height: 1000px;
    transition: max-height 0.3s;
}

.accordion--content p {
    font-style: normal;
    font-weight: 500;
    margin: 0;
    font-size: 20px;
    line-height: 1.4;
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

.accordion--header.open p {
    color: var(--blue-primary-);
}

@media (max-width: 1200px) {
    .accordion--header {
        padding: 15px 0;
    }

    .accordion--header p {
        font-size: 24px;
    }

    .accordion--content {
        margin-top: 30px;
    }

    .accordion--content p {
        font-size: 18px;
    }
}

@media (max-width: 992px) {
    .accordion--header p {
        font-size: 22px;
    }
}

@media (max-width: 768px) {
    .accordion--header p {
        font-size: 20px;
    }

    .accordion--content {
        margin-top: 25px;
    }

    .accordion--content p {
        font-size: 16px;
    }
}

@media (max-width: 600px) {
    .accordion--header p {
        font-size: 18px;
    }
}

@media (max-width: 468px) {
    .accordion--header p {
        font-size: 16px;
    }

    .accordion--content p {
        font-size: 14px;
    }
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