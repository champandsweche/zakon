<template>
  <div class="accordion">
    <div v-for="item in accordionItems" :key="item.id" class="accordion__item">
      <div
          class="accordion__head"
          @click="toggleAccordion(item.id)"
          :class="{ 'accordion__head--active': isActiveAccordion(item.id) }"
      >
        <h3 class="accordion__title">{{ item.title }}</h3>
      </div>
      <transition name="accordion-transition">
        <div
            class="accordion__body"
            :class="{ 'accordion__body--active': isActiveAccordion(item.id) }"
            :style="bodyStyles(item)"
        >
          <div class="accordion__answer" v-if="item.answer">
            {{ item.answer }}
          </div>
          <div v-if="hasSubItems(item)" class="accordion__sub-items">
            <div
                v-for="subItem in item.subItems"
                :key="subItem.id"
                class="accordion__sub-item"
            >
              <div
                  class="accordion__sub-head"
                  @click="toggleSubAccordion(subItem.id, item.id)"
                  :class="{ 'accordion__sub-head--active': isActiveSubAccordion(subItem.id, item.id) }"
              >
                <span class="accordion__sub-indicator"></span>
                <h4 class="accordion__sub-title">{{ subItem.title }}</h4>
              </div>
              <transition name="accordion-transition">
                <div
                    class="accordion__sub-body"
                    :class="{ 'accordion__sub-body--active': isActiveSubAccordion(subItem.id, item.id) }"
                    :style="bodyStyles(subItem)"
                >
                  <div class="accordion__sub-answer" v-if="subItem.answer">
                    {{ subItem.answer }}
                  </div>
                </div>
              </transition>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    accordionItems: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      activeAccordionIds: [],
    };
  },
  methods: {
    toggleAccordion(id) {
      const index = this.activeAccordionIds.indexOf(id);
      if (index > -1) {
        const item = this.findItemById(id);
        if (item && this.hasSubItems(item)) {
          const subItemIds = item.subItems.map(subItem => subItem.id);
          this.activeAccordionIds = this.activeAccordionIds.filter(accId => !subItemIds.includes(accId));
        }
        this.activeAccordionIds.splice(index, 1);
      } else {
        this.activeAccordionIds = [id];
      }
    },
    toggleSubAccordion(subItemId, parentId, event) {
      const isActiveSubAccordion = this.isActiveAccordion(subItemId);
      const isActiveParentAccordion = this.isActiveAccordion(parentId);
      if (event && event.target && event.target.closest('.accordion__sub-head') && isActiveParentAccordion) {
        return;
      }
      const previousSubItemId = this.activeAccordionIds.find(id => {
        const item = this.findItemById(id);
        return item && this.hasSubItems(item) && this.isActiveAccordion(id) && id !== subItemId && id !== parentId;
      });
      if (previousSubItemId) {
        this.activeAccordionIds = this.activeAccordionIds.filter(id => id !== previousSubItemId);
      }
      if (isActiveSubAccordion) {
        this.activeAccordionIds = this.activeAccordionIds.filter(id => id !== subItemId);
      } else {
        this.activeAccordionIds = this.activeAccordionIds.filter(id => id === parentId || id === subItemId);
        this.activeAccordionIds.push(subItemId);
      }
    },
    findItemById(id) {
      return this.accordionItems.find(item => item.id === id);
    },
    isActiveAccordion(id) {
      return this.activeAccordionIds.includes(id);
    },
    isActiveSubAccordion(subItemId) {
      return this.isActiveAccordion(subItemId);
    },
    hasSubItems(item) {
      return item.subItems && item.subItems.length > 0;
    },
    bodyStyles(item) {
      if (this.isActiveAccordion(item.id)) {
        return {
          maxHeight: "1000px",
          opacity: "1",
          transition: "max-height 1.2s ease, opacity 1.2s ease",
        };
      } else {
        return {
          maxHeight: "0",
          opacity: "0",
          transition: "max-height 0.8s ease, opacity 0.8s ease",
        };
      }
    }
  },
};
</script>

<style scoped>
.accordion {
  display: flex;
  flex-direction: column;
  gap: 80px;
}

.accordion__head,
.accordion__sub-head {
  cursor: pointer;
  position: relative;
  padding-right: 30px;
  transition: color .3s, opacity .3s;
}

.accordion__sub-head {
  color: var(--blue-primary-);
}

.accordion__sub-head:hover {
  color: #242424;
}

.accordion__head:hover,
.accordion__sub-head:hover {
  color: var(--blue-primary-);
}

.accordion__head--active,
.accordion__sub-head--active {
  color: var(--blue-primary-);
}

.accordion__head--active.accordion__head::before,
.accordion__sub-head--active.accordion__sub-head::before {
  opacity: 0;
  transition: opacity .8s;
}

.accordion__head::after,
.accordion__head::before,
.accordion__sub-head::after,
.accordion__sub-head::before {
  content: "";
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  right: 0;
  background-color: var(--blue-primary-);
  transition: opacity .8s;
}

.accordion__head::after,
.accordion__sub-head::after {
  height: 2px;
  width: 20px;
}

.accordion__head::before,
.accordion__sub-head::before {
  width: 2px;
  height: 20px;
  right: 9px;
}

.accordion__title,
.accordion__sub-title {
  font-weight: 400;
  font-size: 22px;
  line-height: 1.3;
}

.accordion__answer {
  margin-top: 25px;
}

.accordion__sub-answer {
  margin-top: 15px;
}

.accordion__answer,
.accordion__sub-answer {
  line-height: 1.4;
  font-size: 18px;
}

.accordion__sub-items {
  margin-top: 35px;
  line-height: 1.3;
}

.accordion__sub-item {
  padding-bottom: 15px;
  border-bottom: 1px solid var(--blue-primary-);
}

.accordion__sub-item:not(:last-child) {
  margin-bottom: 30px;
}

.accordion__body,
.accordion__sub-body {
  overflow: hidden;
}

@media (max-width: 768px) {
  .accordion__title,
  .accordion__sub-title {
    font-size: 20px;
  }

  .accordion__answer,
  .accordion__sub-answer {
    font-size: 16px;
  }

  .accordion__sub-items {
    margin-top: 25px;
  }
}

@media (max-width: 600px) {
  .accordion {
    gap: 50px;
  }

  .accordion__head::after,
  .accordion__sub-head::after {
    width: 16px;
  }

  .accordion__head::before,
  .accordion__sub-head::before {
    height: 16px;
    right: 7px;
  }

  .accordion__title,
  .accordion__sub-title {
    font-size: 18px;
  }

  .accordion__answer,
  .accordion__sub-answer {
    font-size: 14px;
    margin-top: 15px;
  }

  .accordion__sub-items {
    margin-top: 20px;
  }
}

@media (max-width: 468px) {
  .accordion__title,
  .accordion__sub-title {
    font-size: 16px;
  }
}
</style>