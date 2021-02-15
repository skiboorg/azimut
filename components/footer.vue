<template>
  <footer class="footer">
   <div class="container">
     <div class="footer-wrapper">
       <div class="footer-row">

           <img src="/logo.svg" alt="">

         <p>Челябинск,<br>ул. Косарева, д. 75</p>
         <p>с 9:00 до 22:00</p>
         <p><a href="tel:+73512251065">+7 (351) 225-10-65</a></p>
         <p><a href="tel:+7 (982) 363-03-03">+7 (982) 363-03-03</a></p>
         <p><a href="mailto:avto@gcexpress.ru">avto@gcexpress.ru</a></p>
         <el-button id="callbackModal" @click="dialogVisible=true" type="primary">Заказать звонок</el-button>
       </div>
       <div class="footer-row">
         <ul>
           <li><a href="/sitemap.xml" target="_blank">Карта сайта</a></li>
           <li><nuxt-link to="/about">О нас</nuxt-link></li>
           <li><nuxt-link to="/services">Услуги</nuxt-link></li>
           <li><nuxt-link to="/cars">Автопарк</nuxt-link></li>
           <li><nuxt-link to="/outsourcing-outstaffing">Аутсортсинг</nuxt-link></li>
           <li><nuxt-link to="/prices">Цены и оплата</nuxt-link></li>
<!--           <li><nuxt-link to="/1">Отзывы</nuxt-link></li>-->
           <li><nuxt-link to="/contact">Контакты</nuxt-link></li>
         </ul>
       </div>
       <div class="footer-row">
          <ul class="footer-row-colums">
            <li><nuxt-link :to="`/services/${service.name_slug}`" v-for="service in services" :key="service.id">{{service.name}}</nuxt-link></li>

            <li><nuxt-link to="/1">Политика конфиденциальности</nuxt-link></li>
            <li><nuxt-link to="/1">Пользовательское соглашение</nuxt-link></li>
            <li><nuxt-link to="/1">Публичная оферта</nuxt-link></li>

          </ul>
       </div>
     </div>
   </div>

      <el-dialog class="modal" :visible.sync="dialogVisible" >
        <p class="modal-title">Укажите свой номер телефона и мы вам перезвоним</p>
        <el-input v-model="phone" placeholder="Ваш номер телефона"></el-input>
        <el-input ref="ttt" style="display: none" id="carID" v-model="car_id" value="123" placeholder="Ваш номер телефона"></el-input>

          <el-button style="width: 100%;margin-bottom: 20px" type="primary">Оставить заявку</el-button>
      <el-checkbox v-model="agree">Даю согласие на обработку<br> персональных данных</el-checkbox>

</el-dialog>


  </footer>
</template>

<script>
  export default {
     async asyncData({$axios}){

    try{
      const get_services = await $axios.get(`/api/get_services`)
      const services = get_services.data
      return {services}//,banners
    }catch (e) {
      const err = 404
      return {err}
    }
  },
  data() {
      return {
        dialogVisible:false,
        agree:false,
        phone:null,
        car_id:null,

      }
    },
  };
</script>
