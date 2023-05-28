<template>
  <div class="section--application">
    <div class="container">
      <div class="inner--header">
        <div class="title">
          <span class="title__number">03</span>
          <div class="title__content">
            <p>Заполните заявку на консультацию</p>
            <div class="title__progress">
              <span></span>
              <span></span>
            </div>
          </div>
        </div>
        <div class="application--content">
          <h2>Заполните заявку и мы свяжемся с вами в течение 30 минут</h2>
          <div class="content--inner">
            <div class="content--left-side">
              <form class="application--content__contact" @submit.prevent="submitForm" id="contact">
                <ul class="application__list">
                  <li class="item">
                    <input
                        type="text"
                        placeholder="Ваше имя"
                        v-model="name"
                        @input="removeError('name')"
                        ref="nameInput"
                        :class="{ 'input--error': showError && !nameFilled }"
                    />
                    <span v-if="!nameFilled && showError" class="error-message">Имя не соответствует требованиям заполнения</span>
                  </li>
                  <li class="item">
                    <input
                        type="text"
                        placeholder="Ваша фамилия"
                        v-model="surname"
                        @input="removeError('surname')"
                        ref="surnameInput"
                        :class="{ 'input--error': showError && !surnameFilled }"
                    />
                    <span v-if="!surnameFilled && showError" class="error-message">Фамилия не соответствует требованиям заполнения</span>
                  </li>
                  <li class="item">
                    <input
                        class="footer__form-field"
                        type="tel"
                        placeholder="Ваш телефон"
                        v-model="phone"
                        @input="formatPhoneNumber"
                        ref="phoneInput"
                        :class="{ 'input--error': showError && $refs.phoneInput && $refs.phoneInput.classList.contains('input--error') }"
                        @blur="validatePhoneNumber"
                        data-tel-input
                    />
                    <span v-if="showError && $refs.phoneInput && $refs.phoneInput.classList.contains('input--error')"
                          class="error-message">Номер телефона не соответствует требованиям</span>
                  </li>
                </ul>
                <span class="success--alert" v-if="success">Форма успешно отправлена</span>
                <div class="custom-select">
                  <div class="select--header" :class="{ active: isSelectOpen }" @click="toggleSelect">
                    <p>{{
                        selectedSubItem ? selectedSubItem.name : (selectedService ? selectedService.name : 'Выберите услугу')
                      }}</p>
                    <svg width="14" height="8" viewBox="0 0 14 8" fill="none"
                         xmlns="http://www.w3.org/2000/svg" :class="{ rotate: isSelectOpen }">
                      <path d="M13 1.5L7 6.5L1 1.5" stroke="#F9FBFE" stroke-width="2"
                            stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                  </div>
                  <div class="select--content" :class="{ active: isSelectOpen }">
                    <div class="content--item" v-for="item in items" :key="item.id"
                         @click="selectItem(item)">
                      <p>{{ item.name }}</p>
                      <div v-if="item.subItems" class="sub-items">
                        <div class="sub-items__element" v-for="subItem in item.subItems"
                             :key="subItem.id" @click="selectSubItem(subItem)">
                          <p>{{ subItem.name }}</p>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="custom-checkbox">
                  <input class="custom-checkbox__input" type="checkbox" v-model="checkboxChecked"
                         @change="removeErrorCheckbox" ref="checkboxInput"
                         :class="{ 'input--error': checkboxChecked }"/>
                  <span class="checkmark"></span>
                  <label class="custom-checkbox__label" for="custom-checkbox__label">Согласен на
                    обработку персональных
                    данных</label>
                </div>
                <button class="btn" type="submit">
                  <div class="btn--arrow">
                    <svg
                        width="19"
                        height="10"
                        viewBox="0 0 19 10"
                        fill="none"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                          d="M17.9419 5.44194C18.186 5.19786 18.186 4.80214 17.9419 4.55806L13.9645 0.580583C13.7204 0.336505 13.3247 0.336505 13.0806 0.580583C12.8365 0.82466 12.8365 1.22039 13.0806 1.46447L16.6161 5L13.0806 8.53553C12.8365 8.77961 12.8365 9.17534 13.0806 9.41942C13.3247 9.6635 13.7204 9.6635 13.9645 9.41942L17.9419 5.44194ZM0.5 5.625H17.5V4.375H0.5V5.625Z"
                          fill="#F9FBFE"
                      />
                    </svg>
                  </div>
                  Отправить
                </button>
              </form>
            </div>
            <div class="content--right-side">
              <img :src="img" alt="">
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SectionApplication",
  data() {
    return {
      success: false,
      items: [
        {
          id: 1,
          name: "Административное право",
          subItems: [
            {id: 1, name: 'Составление жалоб'},
            {id: 2, name: 'Составление ходатайств'},
            {id: 3, name: 'Составление исковых заявлений'},
            {id: 4, name: 'Представительство в суде'},
            {id: 5, name: 'Обжалование штрафов'},
            {id: 6, name: 'Помощь по вопросам миграции'},
          ],
        },
        {
          id: 2,
          name: "Трудовое право",
          subItems: [
            {id: 1, name: 'Оспаривание незаконного увольнения'},
            {id: 2, name: 'Взыскание заработной платы'},
            {id: 3, name: 'Составление жалоб'},
            {id: 4, name: 'Составление ходатайств'},
            {id: 5, name: 'Составление исковых заявлений'},
            {id: 6, name: 'Представительство в суде'},
            {id: 7, name: 'Взыскание компенсаций'},
          ],
        },
        {
          id: 3,
          name: "Семейное право",
          subItems: [
            {id: 1, name: 'Выяснение правовой позиции'},
            {id: 2, name: 'Консультация'},
            {id: 3, name: 'Писменная консультация\n'},
            {id: 4, name: 'Написание искового заявления на расторжение брака'},
            {id: 5, name: 'Написание искового заявление на алименты'},
            {id: 6, name: 'Написание искового заявления на установление отцовства'},
            {
              id: 7,
              name: 'Написание возражения на исковое заявление по установлению отцовства и факта родственных отношении'
            },
            {id: 8, name: 'Написание искового заявления на раздел имущества'},
            {id: 9, name: 'Написание возражения на исковое заявление по разделу имущества'},
            {id: 10, name: 'Представительство в суде первой инстанции по расторжению брака'},
            {id: 11, name: 'Представительство в суде первой инстанции по установлению алиментов'},
            {
              id: 12,
              name: 'Представительство в суде первой инстанции по установлению отцовства и родственных отношении'
            },
            {id: 13, name: 'Представительство в суде первой инстанции по разделу имущества'},
            {id: 14, name: 'Написание искового заявления о признании брака фиктивным'},
            {id: 15, name: 'Представительство в суде первой инстанции о признании брака фиктивным'}
          ],
        },
        {
          id: 4,
          name: "Автомобильное право",
          subItems: [
            {id: 1, name: 'Оспаривание штрафов'},
            {id: 2, name: 'Защита виновника ДТП'},
            {id: 3, name: 'Взыскание ущерба с виновника ДТП'},
            {id: 4, name: 'Страховые споры'},
            {id: 5, name: 'Взыскание страховых выплат'},
            {id: 6, name: 'Снятие с регистрационного учёта'},
            {id: 7, name: 'Выезд на место ДТП'},
            {id: 8, name: 'Оспаривание сделок'},
            {id: 9, name: 'Правовая экспертиза документов'},
            {id: 10, name: 'Представительство в суде'},
          ],
        },
        {
          id: 5,
          name: "Земельное право",
          subItems: [
            {id: 1, name: 'Сопровождение сделок с недвижимостью'},
            {id: 2, name: 'Изменение вида разрешённого использования земли'},
            {id: 3, name: 'Представительство в суде'},
            {id: 4, name: 'Составление исковых заявлений'},
            {id: 5, name: 'Юридическая проверка недвижимости'},
            {id: 6, name: 'Снятие ареста с имущества'},
            {id: 7, name: 'Раздел имущества'},
            {id: 8, name: 'Признание права собственности'},
            {id: 9, name: 'Регистрация права собственности на земельный участок'},
            {id: 10, name: 'Оформление документов на землю'},
            {id: 11, name: 'Оформление участка под домом'},
            {id: 12, name: 'Оформление разрешений на строительство'},
          ],
        },
        {
          id: 6,
          name: "Банкротство и кредиты",
          subItems: [
            {id: 1, name: 'Банкротство физических лиц'},
            {id: 2, name: 'Ликвидация организаций'},
            {id: 3, name: 'Представительство в суде'},
            {id: 4, name: 'Банкротство юридических лиц'},
            {id: 5, name: 'Подготовка документов в суд'},
            {id: 6, name: 'Составление ходатайств'},
            {id: 7, name: 'Отмена судебных решений'},
            {id: 8, name: 'Обжалование действий приставов'},
          ],
        }
      ],
      img: "../public/img/sectionApplication/img.svg",
      selectedService: null,
      isSelectOpen: false,
      name: "",
      surname: "",
      phone: "",
      nameFilled: false,
      surnameFilled: false,
      phoneFilled: false,
      checkboxChecked: false,
      showError: false,
    };
  },
  methods: {
    toggleSelect() {
      this.isSelectOpen = !this.isSelectOpen;
      if (!this.isSelectOpen) {
        this.selectedSubItem = null;
      }
    },
    selectItem(item) {
      if (item.subItems && item.subItems.length > 0) {
        if (this.selectedSubItem && this.selectedSubItem.parentId === item.id) {
          this.selectedService = item;
        } else {
          this.selectedService = item;
          if (!item.subItems || !item.subItems.includes(this.selectedSubItem)) {
            this.selectedSubItem = item.subItems ? item.subItems[0] : null;
          }
        }
      } else {
        this.selectedService = item;
        this.selectedSubItem = null;
        this.isSelectOpen = false;
      }
    },
    selectSubItem(subItem) {
      this.selectedSubItem = subItem;
      this.isSelectOpen = false;
    },
    submitForm() {
      this.nameFilled = this.name.trim().length >= 2 && /^[\u0400-\u04FF]+$/.test(this.name.trim());
      this.surnameFilled = this.surname.trim().length >= 4 && /^[\u0400-\u04FF]+$/.test(this.surname.trim());
      this.showError = true;

      if (this.nameFilled && this.surnameFilled && (this.phone === '' || this.validatePhoneNumber()) && this.checkboxChecked) {
        const formData = new FormData();
        formData.append("name", this.name);
        formData.append("surname", this.surname);
        formData.append("phone", this.phone);

        if (this.selectedService) {
          formData.append('selectedService', this.selectedService.name);
        }
        if (this.selectedSubItem) {
          formData.append('selectedSubItem', this.selectedSubItem.name);
        }

        fetch("func.php", {
          method: "POST",
          body: formData
        })
            .then(response => {
              this.success = true;

              setTimeout(() => {
                this.success = false;
              }, 3000);
            })
            .catch(error => {

            });
        console.log('FormData:', Object.fromEntries(formData));
      } else {
        if (!this.nameFilled) {
          this.$refs.nameInput.classList.add("input--error");
        }
        if (!this.surnameFilled) {
          this.$refs.surnameInput.classList.add("input--error");
        }
        if (!this.validatePhoneNumber()) {
          this.$refs.phoneInput.classList.add("input--error");
        }
        if (!this.checkboxChecked) {
          this.$refs.checkboxInput.classList.add('input--error');
        } else {
          this.$refs.checkboxInput.classList.remove('input--error');
        }

        const firstError = this.nameFilled
            ? this.surnameFilled
                ? "phoneFilled"
                : "surnameFilled"
            : "nameFilled";
        this.$nextTick(() => {
          if (this.$refs[firstError + "Input"]) {
            this.$refs[firstError + "Input"].focus();
          }
        });
      }
    },
    removeError(fieldName) {
      if (fieldName === 'name') {
        this.$refs.nameInput.classList.remove('input--error');
      } else if (fieldName === 'surname') {
        this.$refs.surnameInput.classList.remove('input--error');
      } else if (fieldName === 'phone') {
        this.$refs.phoneInput.classList.remove('input--error');
        this.showError = false;
      }
    },
    removeErrorCheckbox() {
      this.$refs.checkboxInput.classList.remove('input--error');
    },
    formatPhoneNumber(event) {
      let phoneNumber = event.target.value.replace(/\D/g, '');
      let formattedPhoneNumber = '';
      const selectionStart = event.target.selectionStart;

      if (!phoneNumber) {
        this.phone = '';
        return;
      }

      if (event.target.value.length === selectionStart) {
        if (['7', '8', '9'].includes(phoneNumber[0])) {
          if (phoneNumber[0] === '9') {
            phoneNumber = '7' + phoneNumber;
          }
          formattedPhoneNumber = ('8' === phoneNumber[0] ? '8' : '+7') + ' ';
          if (phoneNumber.length > 1) {
            formattedPhoneNumber += '(' + phoneNumber.substring(1, 4);
          }
          if (phoneNumber.length >= 5) {
            formattedPhoneNumber += ') ' + phoneNumber.substring(4, 7);
          }
          if (phoneNumber.length >= 8) {
            formattedPhoneNumber += '-' + phoneNumber.substring(7, 9);
          }
          if (phoneNumber.length >= 10) {
            formattedPhoneNumber += '-' + phoneNumber.substring(9, 11);
          }
        } else {
          formattedPhoneNumber = '+' + phoneNumber.substring(0, 16);
        }
        this.phone = formattedPhoneNumber;
      } else if (event.data && /\D/g.test(event.data)) {
        this.phone = phoneNumber;
      }
    },
    handleBackspace(event) {
      const phoneNumber = event.target.value.replace(/\D/g, '');
      if (event.keyCode === 8 && phoneNumber.length === 1) {
        this.phone = '';
      }
    },
    handlePaste(event) {
      const clipboardData = event.clipboardData || window.clipboardData;
      const phoneNumber = event.target.value.replace(/\D/g, '');
      if (clipboardData) {
        const pastedData = clipboardData.getData('Text');
        if (/\D/.test(pastedData)) {
          this.phone = phoneNumber;
        }
      }
    },
    validatePhoneNumber() {
      const phoneNumber = this.phone.replace(/\D/g, '');
      const isValidPhoneNumber = phoneNumber.length >= 11 && phoneNumber.length <= 14;
      if (isValidPhoneNumber) {
        this.removeError('phone');
      }
      return isValidPhoneNumber;
    }
  },
  mounted() {
    const inputElement = document.querySelector("input[data-tel-input]");
    inputElement.addEventListener('keydown', this.handleBackspace);
    inputElement.addEventListener('paste', this.handlePaste);
  },
  beforeUnmount() {
    const inputElement = document.querySelector("input[data-tel-input]");
    inputElement.removeEventListener('keydown', this.handleBackspace);
    inputElement.removeEventListener('paste', this.handlePaste);
  }
};
</script>

<style scoped>
.section--application--inner {
  margin-top: 350px;
}

.application--content {
  margin-top: 120px;
}

.application__list {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.application--content h2 {
  font-style: normal;
  font-weight: 700;
  font-size: 40px;
  line-height: 1.3;
  display: flex;
  align-items: center;
  font-feature-settings: 'kern' off;
  color: var(--blue-secondary-);
  max-width: 1000px;
}

.content--inner {
  margin-top: 90px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 70px;
}

.content--left-side {
  max-width: 450px;
  width: 100%;
}

.content--left-side form {
  display: flex;
  flex-direction: column;
  gap: 50px;
}

.content--left-side form input {
  align-items: center;
  padding: 25px;
  gap: 10px;
  width: 100%;
  background: var(--gray-);
  border-radius: 25px;
  border: 1px solid var(--gray-);
  transition: border .3s;
}

.content--left-side form input:focus {
  background: transparent;
  border: 1px solid var(--blue-secondary-);
  border-radius: 25px;
  color: var(--blue-secondary-);
}

.input--error {
  border: 1px solid red !important;
  background: transparent !important;
  transition: color .3s;
}

.input--error::placeholder {
  color: red !important;
}

.error-message {
  color: red;
  display: block;
  max-width: 450px;
  margin-top: 10px;
}

.success--alert {
  background-color: #A7FFBA;
  border-radius: 5px;
  padding: 25px 13px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.success--alert p {
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  text-align: center;
}

.select--header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 25px;
  gap: 10px;
  background: var(--blue-secondary-);
  border-radius: 25px;
  cursor: pointer;
}

.select--header svg {
  transition: transform .3s;
}

.select--header p {
  font-style: normal;
  font-weight: 700;
  font-size: 20px;
  color: var(--white-);
  transition: transform 0.3s ease;
}

.select--header.active svg {
  transform: rotate(180deg);
}

.select--content {
  margin-top: 20px;
  flex-direction: column;
  align-items: flex-start;
  padding: 0;
  background: var(--gray-);
  border-radius: 25px 0 0 25px;
  display: none;
  opacity: 0;
  z-index: -20;
  width: 100%;
  max-width: 450px;
  max-height: 0;
  overflow-y: scroll;
  transition: max-height 0.3s ease, opacity 0.3s ease;
}

.select--content.active {
  position: absolute;
  display: block;
  z-index: 100;
  opacity: 1;
  max-height: 300px;
}

.select--content.active::-webkit-scrollbar {
  width: 6px;
}

.select--content.active::-webkit-scrollbar-track {
  background-color: rgb(13, 56, 169);
}

.select--content.active::-webkit-scrollbar-thumb {
  background-color: var(--blue-primary-);
}

.content--item {
  padding: 30px;
  border-bottom: 2px solid rgba(106, 153, 230, 0.1);
  cursor: pointer;
  transition: background-color .3s, color .3s;
  background-color: var(--gray-);
}

.content--item:hover {
  background-color: var(--blue-primary-);
  color: var(--white-);
}

.content--item:hover .sub-items {
  color: var(--white-);
}

.content--item:last-child {
  border-bottom: none;
}

.sub-items {
  margin-left: 15px;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  line-height: 1.4;
}

.sub-items__element {
  transition: color .3s;
  padding: 10px 0;
}

.sub-items__element:hover {
  color: var(--dark-);
}

@media (max-width: 1400px) {
  .application--content h2 {
    font-size: 34px;
  }
}

@media screen and (max-width: 1200px) {
  .application--content h2 {
    text-align: center;
    font-size: 30px;
  }

  .content--inner {
    flex-direction: column-reverse;
    margin-top: 60px;
  }

  .content--right-side img {
    width: 420px;
    height: 460px;
  }

  .content--left-side {
    max-width: 600px;
    width: 100%;
  }

  .select--content {
    max-width: 100%;
  }

  .select--content.active {
    position: static;
  }
}

@media (max-width: 992px) {
  .application--content {
    margin-top: 90px;
  }

  .application--content h2 {
    font-size: 26px;
    max-width: 500px;
    margin: 0 auto;
  }
}

@media (max-width: 768px) {
  .application--content {
    margin-top: 65px;
  }

  .application--content h2 {
    font-size: 22px;
    max-width: 450px;
  }

  .content--right-side img {
    width: 360px;
    height: 370px;
  }

  .select--header p {
    font-size: 18px;
  }

  .application__list {
    gap: 20px;
  }

  .content--left-side form {
    gap: 40px;
  }

  .select--content {
    font-size: 14px;
  }

  .custom-checkbox__label {
    font-size: 14px;
  }
}

@media (max-width: 600px) {
  .application--content h2 {
    font-size: 20px;
  }

  .content--inner {
    margin-top: 40px;
  }

  .content--right-side img {
    width: 320px;
    height: 330px;
  }

  .select--header p {
    font-size: 16px;
  }
}

@media (max-width: 468px) {
  .application--content {
    margin-top: 45px;
  }

  .application--content h2 {
    font-size: 18px;
  }
}
</style>
