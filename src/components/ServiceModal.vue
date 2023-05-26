<template>
    <div class="modal" :class="{ 'modal--active': modalVisible }">
        <div class="modal__inner">
            <h2 class="modal__title">{{ card.title }}</h2>
            <p class="modal__text">{{ card.description }}</p>
            <span class="modal__price">Цена - от <span>{{ card.price }}₽</span> за услугу</span>
            <button class="modal__btn" @click="closeModal">Закрыть</button>
        </div>
    </div>
</template>

<script>
export default {
    props: ['card'],
    data() {
        return {
            modalVisible: true,
        };
    },
    methods: {
        closeModal() {
            this.modalVisible = false;
            document.body.classList.remove('modal-open');
            this.$emit('close-modal');
        },
    },
};
</script>

<style>
.modal {
    padding: 0 15px;
    max-width: 1000px;
    width: 100%;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s, visibility 0.3s;
}

.modal__inner {
    background-color: #fff;
    padding: 50px;
    overflow-y: auto;
    border-radius: 15px;
}

.modal--active {
    opacity: 1;
    visibility: visible;
    z-index: 100;
}

.modal__title {
    font-size: 26px;
    margin-bottom: 30px;
    font-weight: 700;
    color: var(--blue-primary-);
}

.modal__text {
    font-size: 18px;
    line-height: 1.4;
    margin-bottom: 40px;
}

.modal__price {
    display: block;
    font-weight: 500;
    margin-bottom: 60px;
    font-size: 20px;
}

.modal__price span {
    color: var(--blue-primary-)
}

.modal__btn {
    padding: 18px 50px;
    line-height: 1;
    min-width: 240px;
    border-radius: 10px;
    border: 1px solid var(--blue-primary-);
    transition: color .3s, background-color .3s;
}

.modal__btn:hover {
    color: var(--white-);
    background-color: var(--blue-primary-);
}

@media (max-width: 1200px) {
    .modal__inner {
        padding: 40px;
    }

    .modal__title {
        margin-bottom: 20px;
    }

    .modal__price {
        font-size: 18px;
    }
}

@media (max-width: 768px) {
    .modal__inner {
        padding: 35px;
    }

    .modal__title {
        font-size: 24px;
    }

    .modal__text {
        font-size: 16px;
    }

    .modal__price {
        margin-bottom: 40px;
    }

    .modal__btn {
        padding: 18px 30px;
    }
}

@media (max-width: 600px) {
    .modal__inner {
        padding: 30px;
    }

    .modal__title {
        font-size: 22px;
    }

    .modal__btn {
        padding: 16px 30px;
    }
}

@media (max-width: 468px) {
    .modal__inner {
        padding: 25px;
    }

    .modal__title {
        font-size: 20px;
    }

    .modal__text {
        font-size: 14px;
    }

    .modal__price {
        font-size: 16px;
    }
}
</style>
