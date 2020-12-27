<template>
  <div>

    <section>
      <div class="container">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item>Наши услуги</el-breadcrumb-item>
        </el-breadcrumb>
      </div>

      <div class="container page-container">
        <h1 class="section-title">Услуги</h1>
        <p class="mb-40">Специализируясь на пассажирских перевозках в одном из крупнейших городов России – Челябинске, Группа Компаний «Экспресс» зарекомендовала себя как надежный партнер, сотрудничать с которым выгодно и комфортно. Наша команда работает на благо жителей Челябинской области уже свыше 9 лет, что позволило стать примером качественного сервиса, как в сфере пассажирских перевозок, так и в сфере аренды автобусов различной вместимости.</p>
        <div class="services">
          <div @click="$router.push(`/services/${service.name_slug}`)"  class="services-item" v-for="service in services" :key="service.id">
            <img :src="service.img" alt="">
            <p>{{service.name}}</p>
          </div>
        </div>
        <div class="text-center"><el-button type="primary">Заказать авто</el-button></div>
      </div>

    </section>

  </div>

</template>

<script>
  export default {
    data:function(){
      return{

        services:[
          {id:1,img:'http://placehold.it/300',name_slug:'123',name:'Аутсорсинг и аутстаффинг водителей'},
          {id:2,img:'http://placehold.it/300',name_slug:'123',name:'Аренда автомобилей для деловых встреч и мероприятий'},
          {id:3,img:'http://placehold.it/300',name_slug:'123',name:'Трансфер в аэропорт и на железнодорожный вокзал'},
          {id:4,img:'http://placehold.it/300',name_slug:'123',name:'Аутсорсинг и аутстаффинг водителей'},
        ],


      }
    },
  }
</script>


