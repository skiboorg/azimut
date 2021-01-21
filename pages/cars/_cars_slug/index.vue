<template>
  <div>
    <section>
      <div class="container mb-40">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item :to="{ path: '/cars' }">Автопарк</el-breadcrumb-item>
          <el-breadcrumb-item>{{category.name}} </el-breadcrumb-item>
        </el-breadcrumb>
      </div>
    <div class="container ">
      <h1 class="section-title ">{{category.name}}</h1>
    <div class="service-wrapper">
        <div class="service-left">
          <div @click="currentSubcat=index" class="service-item" v-for="(subcat,index) in category.subcategory" :key="subcat.id">
            <p>{{subcat.name}}</p>

          </div>
        </div>
        <div class="service-right">
            <div class="cars-wrapper">

<!--              <div-->
<!--                   class="car-item" v-for="car in category.subcategory[currentSubcat].cars" :key="car.id">-->
<!--                <nuxt-link :to="`/cars/${categoryNameSlug}/${car.name_slug}`" >-->
<!--                <img :src="car.images[0].image" alt="">-->
<!--                <p class="car-item__name">{{car.name}}</p>-->
<!--                <div class="car-item__group">-->
<!--                  <p>от {{car.min_hour}} ч.</p>-->
<!--                  <p>Мест: {{car.seats}}</p>-->
<!--                </div>-->
<!--                <div class="car-item__group">-->
<!--                  <p v-if="car.price_km" class="text-bold">{{car.price_km}}р/км</p>-->
<!--                  <p v-if="car.price_hour"  class="text-bold">{{car.price_hour}}р/час</p>-->
<!--                </div>-->
<!--                </nuxt-link>-->
<!--                <div class="car-item__group">-->
<!--                  <el-button type="primary">Заказать</el-button>-->
<!--                  <nuxt-link :to="`/cars/${categoryNameSlug}/${car.name_slug}`" >-->
<!--                  <el-button plain type="primary">Подробнее</el-button>-->
<!--                  </nuxt-link>-->

<!--                </div>-->

<!--              </div>-->
              <CarCard v-for="car in category.subcategory[currentSubcat].cars" :key="car.id" :car="car"/>
            </div>
        </div>
      </div>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias animi cupiditate doloremque facilis libero magnam necessitatibus, perferendis quibusdam quidem saepe.</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias animi cupiditate doloremque facilis libero magnam necessitatibus, perferendis quibusdam quidem saepe.</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias animi cupiditate doloremque facilis libero magnam necessitatibus, perferendis quibusdam quidem saepe.</p>

    </div>
  </section>

  </div>

</template>

<script>
  import CarCard from '@/components/CarCard';

  export default {
    components:{
            CarCard

        },
     async asyncData({$axios,params}){

      console.log(params)
      const get_category= await $axios.get(`/api/get_category?name_slug=${params.cars_slug}`)
      const category = get_category.data
      console.log(category)
      return {category}//,banners

  },
    data:function(){
      return{
        currentSubcat:0,
        categoryNameSlug:this.$route.params.cars_slug,
        services:[
          {id:1,img:'http://placehold.it/300',name_slug:'123',name:'Аутсорсинг и аутстаффинг водителей'},
          {id:2,img:'http://placehold.it/300',name_slug:'123',name:'Аренда автомобилей для деловых встреч и мероприятий'},
          {id:3,img:'http://placehold.it/300',name_slug:'123',name:'Трансфер в аэропорт и на железнодорожный вокзал'},
          {id:4,img:'http://placehold.it/300',name_slug:'123',name:'Аутсорсинг и аутстаффинг водителей'},
        ],
          cars:[
          {id:1,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'1000',price_per_hour:'1000'},
          {id:2,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'7000',price_per_hour:'7000'},
          {id:3,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроghjhgjhgjhgjhgjавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'1000',price_per_hour:'1000'},
          {id:4,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'1000',price_per_hour:'1000'},
          {id:5,img:'http://placehold.it/300',category:'123',name_slug:'sdfdsf',name:'Микроавтобус Ситроен',time:'от 3 часов',places:'17 мест',price_per_km:'1000',price_per_hour:'1000'}
        ],

      }
    },
  }
</script>


