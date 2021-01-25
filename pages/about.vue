<template>
  <div>
    <section>
       <div class="container">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item>О нас</el-breadcrumb-item>
        </el-breadcrumb>
      </div>
    <div class="container page-container">
      <h1 class="section-title">О компании</h1>
      <img rel="preload" class="mb-40" src="/vodila.jpg" alt="">
      <p>В компании работают специалисты и водители с большим опытом работы, автопарк оснащен современными моделями
        автомобилей от эконом до премиум класса, услуги оказываются в соответствии с требованиями безопасности, компания
        работает на рынке более 8 лет, персональный подход к каждому клиенту.</p>
    </div>

  </section>
  <section>
    <div class="container">
       <div class="features">
        <div class="features-item" v-for="feature in features" :key="feature.id">
          <img :src="feature.img" alt="">
          <p>{{feature.text}}</p>
        </div>
      </div>
    </div>
  </section>
  </div>

</template>

<script>
  export default {
    data:function(){
      return{

       features:[
          {id:1,text:'В компании работают специалисты и водители \n' +
              'с большим опытом работы',img:'/f1.png'},
          {id:2,text:'Автопарк оснащен современными моделями автомобилей от эконом до премиум-класса',img:'/f2.png'},
          {id:3,text:'Услуги оказываются \n' +
              'в соответствии с требованиями безопасности',img:'/f3.png'},
          {id:4,text:'Компания работает \n' +
              'на рынке более 8 лет',img:'/f4.png'},
          {id:5,text:'Персональный подход к каждому клиенту',img:'/f5.png'},
        ],


      }
    },
  }
</script>


