<template>
    <div class="app">
        <Header/>
        <main class="main">
            <section class="section--header">
                <SectionHeader/>
            </section>

            <section class="section--service" id="services">
                <SectionService @open-modal="openModal"/>
            </section>

            <section class="section--about" id="about">
                <SectionAbout/>
            </section>
            <img class="bg--el" :src="bgEl" alt="Декоративный элемент">
            <section class="section--contact">
                <SectionApplication/>
            </section>

            <section class="section--help" id="help">
                <SectionHelp/>
            </section>

        </main>
        <footer class="footer" id="footer">
            <Footer/>
        </footer>
    </div>
    <ServiceModal v-if="modalVisible" :card="selectedCard" @close-modal="closeModal"/>
</template>

<script>
import {gsap} from 'gsap';
import {ScrollTrigger} from 'gsap/ScrollTrigger';
import VueScrollTo from 'vue-scrollto';

import '../public/css/reset.css';
import '../public/css/custom-checkbox.css';
import '../public/css/global.css';

import Header from "@/components/Header.vue";
import SectionHeader from "@/sections/SectionHeader.vue";
import SectionService from "@/sections/SectionService.vue";
import SectionAbout from "@/sections/SectionAbout.vue";
import SectionApplication from "@/sections/SectionApplication.vue";
import Footer from "@/sections/Footer.vue";
import SectionHelp from "@/sections/SectionHelp.vue";
import ServiceModal from "@/components/ServiceModal.vue";

export default {
    directives: {
        scrollTo: VueScrollTo,
    },
    data() {
        return {
            bgEl: '/public/img/bg-el.png',
            modalVisible: false,
            selectedCard: null
        }
    },
    components: {
        ServiceModal,
        Header,
        SectionHeader,
        SectionService,
        SectionAbout,
        SectionApplication,
        Footer,
        SectionHelp
    },
    methods: {
        openModal(card) {
            this.selectedCard = card;
            this.modalVisible = true;
            document.body.classList.add('modal-open');
        },
        closeModal() {
            this.modalVisible = false;
            document.body.classList.remove('modal-open');
        }
    },
    mounted() {
        gsap.registerPlugin(ScrollTrigger);
        gsap.from('.section--service', {
            opacity: 0,
            y: 100,
            duration: 1,
            scrollTrigger: {
                trigger: '.section--service',
                start: 'top 80%',
                end: 'bottom 50%',
                toggleActions: 'play none none reset'
            }
        });

        gsap.from('.section--about', {
            opacity: 0,
            y: 100,
            duration: 1,
            scrollTrigger: {
                trigger: '.section--about',
                start: 'top 80%',
                end: 'bottom 50%',
                toggleActions: 'play none none reset'
            }
        });
        gsap.from('.section--application', {
            opacity: 0,
            y: 100,
            duration: 1,
            scrollTrigger: {
                trigger: '.section--application',
                start: 'top 80%',
                end: 'bottom 50%',
                toggleActions: 'play none none reset'
            }
        });
        gsap.from('.section--help', {
            opacity: 0,
            y: 100,
            duration: 1,
            scrollTrigger: {
                trigger: '.section--help',
                start: 'top 80%',
                end: 'bottom 50%',
                toggleActions: 'play none none reset'
            }
        });
    }
}
</script>

<style>
.bg--el {
    position: absolute;
    z-index: -1;
    top: 2800px;
}

body.modal-open {
    overflow: hidden;
}

body.modal-open::after {
    content: "";
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 0;
}
</style>