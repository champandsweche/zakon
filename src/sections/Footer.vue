npm<template>
    <div class="section--footer">
        <div class="container">
            <div class="footer--inner">
                <div class="left-side">
                    <img :src="Logo" alt="" class="logo">
                </div>
                <div class="right-side">
                    <div class="text">
                        <b>Контакты</b>
                        <p>Аристей - юридические услуги</p>
                    </div>
                    <div class="text">
                        <b>+7 (800) 775 02 13</b>
                        <p>г Белореченск, Шалимово 5/1</p>
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

    .logo {
        max-width: 80%;
    }
}
</style>