<template>
  <div>
    <section>
      <div class="container mb-40">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item :to="{ path: '/cars' }">Автопарк</el-breadcrumb-item>
          <el-breadcrumb-item :to="{ path: '/cars/sdf' }">Микроавтобусы</el-breadcrumb-item>
          <el-breadcrumb-item>{{car.name}}</el-breadcrumb-item>
        </el-breadcrumb>
      </div>
      <div class="container ">
        <h1 class="section-title text-left">{{car.name}}</h1>
        <div class="car-wrapper">
          <div class="car-images">
            <div class="car-images__big" :style="'background: url(' + currentImage + ')'">
            </div>
            <div class="car-images__small">
              <img @click="currentImage = image.image" v-if="!image.is_main_img"
                   :src="image.image" alt="" v-for="image in car.images" :key="image.id">

            </div>
          </div>
          <div class="car-info">
            <div class="car-info__text"><p v-html="car.info"></p></div>
            <p class="car-info__title">Доступные функции</p>
            <div class="car-info__features">
              <div class="car-info__features--item" v-for="feature in car.features" :key="feature.id">
                <img :src="feature.image" alt="">
                <p>{{feature.name}}</p>
              </div>
            </div>
            <div class="car-info__price">
              <p>от {{car.price_per_km}}р/км</p>
              <p>от {{car.price_per_hour}}р/час</p>
            </div>
            <el-button type="primary">Заказать авто</el-button>
          </div>
        </div>

      </div>
    </section>
    <section>
      <div class="container">
        <h3 class="section-title">Вас также могут заинтересовать</h3>
        <div class="cars-wrapper">
          <div @click="$router.push(`/cars/${car.category}/${car.name_slug}`)"
               class="car-item" v-for="car in cars" :key="car.id">
            <img :src="car.img" alt="">
            <p class="car-item__name">{{car.name}}</p>
            <div class="car-item__group">
              <p>{{car.time}}</p>
              <p>{{car.places}}</p>
            </div>
            <div class="car-item__group">
              <p class="text-bold">{{car.price_per_km}}р/км</p>
              <p class="text-bold">{{car.price_per_hour}}р/час</p>
            </div>
            <div class="car-item__group">
              <el-button type="primary">Заказать</el-button>
              <el-button plain type="primary">Подробнее</el-button>

            </div>
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
        currentImage:null,
        car:{
          id:1,
          images:[
            {id:1,is_main_img:true,image:'http://placehold.it/900'},
            {id:2,is_main_img:false,image:'http://placehold.it/700'},
            {id:3,is_main_img:false,image:'http://placehold.it/500'},
            {id:3,is_main_img:false,image:'http://placehold.it/600'},
          ],
          name:'Микроавтобус Ситроен',
          name_slug:'sfsfd',
          price_per_hour:'1000',
          price_per_km:'222',
          info:'<p>Информация об автомобиле</p><p>Информация об автомобиле1</p><p>Информация об автомобиле3</p>',
          features:[
            {id:1,image:'http://placehold.it/500',name:'20 мест'},
            {id:2,image:'http://placehold.it/500',name:'Микрофон'},
            {id:3,image:'http://placehold.it/500',name:'DVD'},
            {id:4,image:'http://placehold.it/500',name:'USB'},
            {id:5,image:'http://placehold.it/500',name:'Кондиционер'},

          ]

        },

        cars:[
          {id:1,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'1000',price_per_hour:'1000'},
          {id:2,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'7000',price_per_hour:'7000'},
          {id:3,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроghjhgjhgjhgjhgjавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'1000',price_per_hour:'1000'},
          {id:4,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'1000',price_per_hour:'1000'},
          {id:5,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'1000',price_per_hour:'1000'}
        ],

      }
    },
    mounted() {
      this.currentImage = this.car.images.filter(x => x.is_main_img)[0].image
    }
  }
</script>


