<template>
  <div class="app">
    <Header/>
    <main class="main">

      <section class="section--header">
        <SectionHeader/>
      </section>

      <section class="section--service" id="services">
        <h1 class="title dn">Услуги и цены</h1>
        <SectionService/>
      </section>

      <section class="section--about" id="about">
        <h1 class="title dn">Правовая поддержка от Aristei</h1>
        <SectionAbout/>
      </section>
      <img class="bg--el" :src="bgEl" alt="Декоративный элемент">
      <section class="section--contact">
        <h1 class="title dn">Заполните заявку на консультацию</h1>
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
</template>

<script>
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
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

export default {
  directives: {
    scrollTo: VueScrollTo,
  },
  data() {
    return {
      bgEl: '/public/img/bg-el.png',
    }
  },
  components: {
    Header,
    SectionHeader,
    SectionService,
    SectionAbout,
    SectionApplication,
    Footer,
    SectionHelp
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

<style scoped>
.bg--el {
  position: absolute;
  z-index: -1;
  top: 2800px;
}
</style>