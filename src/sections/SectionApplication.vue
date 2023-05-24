<template>
  <div class="section--application">
    <div class="container">
      <div class="section--application--inner">
        <div class="left-side">
          <b>03</b>
          <div class="title">
            <p>Заполните заявку на консультацию</p>
            <div class="progress-bar">
              <span></span>
              <span></span>
            </div>
          </div>
        </div>
        <div class="application--content">
          <h2>Заполните заявку и мы свяжемся с вами в течение 30 минут</h2>
          <div class="content--inner">
          <div class="content--left-side">
            <form @submit.prevent="submitForm" id="contact">
             <input
                type="text"
                placeholder="Ваше имя"
                v-model="name"
                @input="removeError('name')"
                ref="nameInput"
              />
              <input
                type="text"
                placeholder="Ваша фамилия"
                v-model="surname"
                @input="removeError('surname')"
                ref="surnameInput"
              />
              <input
                type="tel"
                placeholder="+79188888888"
                v-model="phone"
                @input="removeError('phone')"
                ref="phoneInput"
              />
              <span class="success--alert" v-if="success"><p>Форма успешно отправлена</p></span>
              <div class="custom-select">
                <div
                  class="select--header"
                  :class="{ active: isSelectOpen }"
                  @click="toggleSelect"
                >
                  <p>{{ selectedService ? selectedService.name : 'Выберите услугу' }}</p>
                  <svg
                    width="14"
                    height="8"
                    viewBox="0 0 14 8"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                    :class="{ rotate: isSelectOpen }"
                  >
                    <path
                      d="M13 1.5L7 6.5L1 1.5"
                      stroke="#F9FBFE"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                </div>
                <div class="select--content" :class="{ active: isSelectOpen }">
                  <div
                    class="content--item"
                    v-for="item in items"
                    :key="item.id"
                    @click="selectService(item)"
                  >
                    <p>{{ item.name }}</p>
                  </div>
                </div>
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
        },
        {
          id: 2,
          name: "Трудовое право",
        },
        {
          id: 3,
          name: "Семейное право",
        },
        {
          id: 4,
          name: "Автомобильное право",
        },
        {
          id: 5,
          name: "Земельное право",
        },
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
    };
  },
  methods: {
    toggleSelect() {
      this.isSelectOpen = !this.isSelectOpen;
    },
    selectService(item) {
      this.selectedService = item;
      this.isSelectOpen = false;
    },
    submitForm() {
      this.nameFilled = this.name.trim().length >= 2 && /^[\u0400-\u04FF]+$/.test(this.name.trim());
      this.surnameFilled = this.surname.trim().length >= 4 && /^[\u0400-\u04FF]+$/.test(this.surname.trim());
      this.phoneFilled = /^\+?\d{10,15}$/.test(this.phone.trim());

      if (this.nameFilled && this.surnameFilled && this.phoneFilled) {
        console.log("Форма отправлена");

        const formData = new FormData();
        formData.append("name", this.name);
        formData.append("surname", this.surname);
        formData.append("phone", this.phone);
        if (this.selectedService) {
          formData.append("selectedService", this.selectedService.name);
        }

        fetch("func.php", {
          method: "POST",
          body: formData
        })
          .then(response => {
            this.success = true;

            setTimeout(() => {
              this.success = false;
            }, 5000);
          })
          .catch(error => {

          });
      } else {
        if (!this.nameFilled) {
          this.$refs.nameInput.classList.add("input--error");
        }
        if (!this.surnameFilled) {
          this.$refs.surnameInput.classList.add("input--error");
        }
        if (!this.phoneFilled) {
          this.$refs.phoneInput.classList.add("input--error");
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
      if (fieldName === "name") {
        this.$refs.nameInput.classList.remove("input--error");
      } else if (fieldName === "surname") {
        this.$refs.surnameInput.classList.remove("input--error");
      } else if (fieldName === "phone") {
        this.$refs.phoneInput.classList.remove("input--error");
      }
    },
  },
};
</script>


<style scoped>
.section--application--inner {
  margin-top: 350px;
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

.application--content {
  margin-top: 120px;
}
.application--content h2 {
  font-style: normal;
  font-weight: 700;
  font-size: 40px;
  line-height: 49px;
  display: flex;
  align-items: center;
  font-feature-settings: 'kern' off;
  color: var(--blue-secondary-);
  max-width: 1000px;
}

.content--inner {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.content--left-side {
  margin-top: 90px;
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
  max-width: 450px;
  background: var(--gray-);
  border-radius: 25px;
  border: 1px solid var(--gray-);
}
.content--left-side form input:focus{
    background: transparent;
    border: 1px solid var(--blue-secondary-);
    border-radius: 25px;
    color: var(--blue-secondary-);
}
.input--error {
  border: 1px solid red !important;
  background: transparent !important;
}
.input--error::placeholder {
  color: red!important;
}
.success--alert {
  width: 100%;
  background-color: #A7FFBA;
  border-radius: 5px;
  max-width: 450px;
  padding: 25px 13px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.success--alert p {
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 18px;
  text-align: center;
}

.select--header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 25px;
  gap: 10px;
  max-width: 450px;
  background: var(--blue-secondary-);
  border-radius: 25px;
  cursor: pointer;
}

.select--header p {
  font-style: normal;
  font-weight: 700;
  font-size: 20px;
  line-height: 24px;
  color: var(--white-);
  transition: transform 0.3s ease;
}

.select--header.active svg {
  transform: rotate(180deg);
}

.select--content {
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  max-width: 450px;
  background: var(--gray-);
  border-radius: 25px;
  display: none;
  opacity: 0;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease, opacity 0.3s ease;
}

.select--content.active {
     width: 100%;
    max-width: 450px;
    position: absolute;
    display: block;
    opacity: 1;
    max-height: 400px;
}

.content--item {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 40px 20px 20px;
  gap: 10px;
  width: 100%;
  max-width: 450px;
  background: transparent;
  border-bottom: 2px solid rgba(106, 153, 230, 0.1);
  cursor: pointer;
}

.content--item:last-child {
  border-bottom: 0px solid rgba(106, 153, 230, 0.1);
  padding-bottom: 40px;
}

@media screen and (max-width: 1200px) {
  .title p {
    font-size: 32px;
  }
}
@media screen and (max-width: 900px) {
  .content--inner {
    flex-direction: column-reverse;
  }
  .content--left-side form input {
    width: 100%;
    max-width: 800px;
}
}
  @media screen and (max-width: 540px) {
    .select--content.active {
      width: 260px;
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
