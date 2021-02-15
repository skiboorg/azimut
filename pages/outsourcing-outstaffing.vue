<template>
  <div>
    <section>
      <div class="container">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item>Аутсорсинг и аутстаффинг водителей</el-breadcrumb-item>
        </el-breadcrumb>
      </div>
 <div class="container page-container">
      <h1 class="section-title">Аутсорсинг и аутстаффинг водителей</h1>
   <img rel="preload" src="/aut.jpg" class="mb-40" alt="">
      <p>Аутсорсинг и аутстаффинг водителей, трансферы в аэропорт и на железнодорожный вокзал, аренда автомобилей на свадьбу или торжество, аренда автомобилей для деловых встреч и мероприятий, доставка на работу сотрудников предприятий, обслуживание предприятий легковым автомобильным транспортом и микроавтобусами, перевозка артистов и спортсменов, туристические поездки.</p>

    </div>

    </section>
    <section class="callback">
      <div class="container">
        <div class="callback-wrapper">
          <div class="">
             <p>Заявка на аутсорсинг/аутстаффинг водителей</p>
          <p>Оставьте заявку — и мы поможем вам оптимизировать процесс работы</p>
          </div>
         <el-button  @click="openModal" type="primary">Заказать звонок</el-button>
        </div>
      </div>
    </section>

  </div>

</template>

<script>
  export default {
    data(){
      return{
      }
    },
    methods:{
       openModal(){
      document.getElementById('callbackModal').click()

    }
    }
  }
</script>


