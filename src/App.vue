
<template>
  <div class="app">
      <Header/>
    <main class="main">

      <section class="section--header">
        <h1 class="title dn">Экспертные юридические услуги для вашего бизнеса</h1>
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
      <img class="bg--el" :src="bgEl" alt="Декорактивный элемент">
      <section class="section--contact">
        <h1 class="title dn">Заполните заявку на консультацию</h1>
        <SectionApplication/>
      </section>
<<<<<<< HEAD
=======
      <section class="section--help">
        <SectionHelp/>
      </section>
>>>>>>> b4f37a8 (Закон асаÑйт)

    </main>
    <footer class="footer" id="footer">
      <Footer/>
    </footer>
  </div>
</template>
<script>
import VueScrollTo from 'vue-scrollto';
import '../public/css/reset.css';
import '../public/css/global.css';
import Header from "@/components/Header.vue";
import SectionHeader from "@/sections/SectionHeader.vue";
import SectionService from "@/sections/SectionService.vue";
import SectionAbout from "@/sections/SectionAbout.vue";
import SectionApplication from "@/sections/SectionApplication.vue";
import Footer from "@/sections/Footer.vue";
import SectionHelp from "@/sections/SectionHelp.vue";
export default  {
  directives: {
     scrollTo: VueScrollTo,
  },
  data() {
    return {
      bgEl: '/public/img/bg-el.png',
    }
  },
  components: {
    SectionHelp,
    Header,
    SectionHeader,
    SectionService,
    SectionAbout,
    SectionApplication,
    Footer
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
