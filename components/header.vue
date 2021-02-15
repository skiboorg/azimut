<template>
  <header class="header" >
  <div class="container">
    <div class="header-top">
      <div @click="$router.push('/')" class="header-top__logo">
        <img src="/logo.svg" alt="">
      </div>
      <div class="header-top__items">
        <p>Челябинск, ул. Косарева, д. 75</p>
        <p>с 9:00 до 18:00</p>
        <p><a href="mailto:avto@gcexpress.ru">avto@gcexpress.ru</a></p>
      </div>
      <div class="header-top__button">
        <el-button @click="dialogCallBackVisible=true" type="primary">Заказать звонок</el-button>
      </div>
    </div>
    <div class="header-nav">
      <ul>
        <li class="header-nav__item"><nuxt-link to="/about">О нас</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/services">Наши услуги</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/cars">Автопарк</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/outsourcing-outstaffing">Аутсорсинг и аутстаффинг водителей</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/prices">Цены и оплата</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/contact">Политика конфиденциальности</nuxt-link></li>
        <li><div class="header-nav__phones">
          <p><a href="tel:+79823630303">+7 (982) 363-03-03</a></p>
          <p><a href="tel:+73512251065">+7 (351) 225-10-65</a></p>
        </div></li>
      </ul>

    </div>
    <div class="header-mobile">
      <div @click="$router.push('/')" class="header-mobile-logo">
       <img src="/logo.svg" alt="">
      </div>
      <div class="header-mobile-toggle">
        <svg width="39" height="25" viewBox="0 0 39 25" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect width="39" height="3" rx="1" fill="url(#paint0_linear)"/>
            <rect y="11" width="39" height="3" rx="1" fill="url(#paint1_linear)"/>
            <rect y="22" width="39" height="3" rx="1" fill="url(#paint2_linear)"/>
            <defs>
            <linearGradient id="paint0_linear" x1="1.74947e-07" y1="1.47059" x2="39" y2="1.47059" gradientUnits="userSpaceOnUse">
            <stop stop-color="#00BE91"/>
            <stop offset="1" stop-color="#00B091"/>
            </linearGradient>
            <linearGradient id="paint1_linear" x1="1.74947e-07" y1="12.4706" x2="39" y2="12.4706" gradientUnits="userSpaceOnUse">
            <stop stop-color="#00BE91"/>
            <stop offset="1" stop-color="#00B091"/>
            </linearGradient>
            <linearGradient id="paint2_linear" x1="1.74947e-07" y1="23.4706" x2="39" y2="23.4706" gradientUnits="userSpaceOnUse">
            <stop stop-color="#00BE91"/>
            <stop offset="1" stop-color="#00B091"/>
            </linearGradient>
            </defs>
        </svg>
      </div>
    </div>
  </div>
  <el-dialog class="modal" :visible.sync="dialogCallBackVisible" >
       <el-input v-model="name" placeholder="Ваше имя"></el-input>
        <el-input v-model="phone" placeholder="Ваш номер телефона"></el-input>
    <el-input type="textarea" rows="5" resize="none" v-model="text" placeholder="Текст сообщения"></el-input>
          <el-button type="primary">Оставить заявку</el-button>

</el-dialog>
  </header>
</template>

<script>

  export default {
    components: {

    },

    data() {
      return {
        dialogCallBackVisible:false,
        name:null,
        phone:null,
        text:null
      }
    },
    watch: {
      '$route.path': function(val) {

      }
    },

    methods: {


    }
  }
</script>



