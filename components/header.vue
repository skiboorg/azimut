<template>
  <header class="header" >
  <div class="container">
    <div class="header-top">
      <div class="header-top__logo">
        <nuxt-link to="/"><img src="http://placehold.it/100" alt=""></nuxt-link>
      </div>
      <div class="header-top__items">
        <p>Челябинск, ул. Косарева, д. 75</p>
        <p>с 9:00 до 18:00</p>
        <p><a href="mailto:avto@gcexpress.ru">avto@gcexpress.ru</a></p>
      </div>
      <div class="header-top__button">
        <el-button type="primary">Заказать звонок</el-button>
      </div>
    </div>
    <div class="header-nav">
      <ul>
        <li class="header-nav__item"><nuxt-link to="/about">О нас</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/services">Наши услуги</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/cars">Автопарк</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/outsourcing-outstaffing">Аутсорсинг и аутстаффинг водителей</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/faq">Цены и оплата</nuxt-link></li>
        <li class="header-nav__item"><nuxt-link to="/contact">Контакты</nuxt-link></li>
        <li><div class="header-nav__phones">
          <p><a href="tel:+79823630303">+7 (982) 363-03-03</a></p>
          <p><a href="tel:+73512251065">+7 (351) 225-10-65</a></p>
        </div></li>
      </ul>

    </div>
  </div>

  </header>
</template>

<script>

  export default {
    components: {

    },

    data() {
      return {

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



