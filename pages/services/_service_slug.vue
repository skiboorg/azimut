<template>
  <div>
    <section>
      <div class="container mb-40">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item :to="{ path: '/services' }">Наши услуги</el-breadcrumb-item>
          <el-breadcrumb-item>Название услуги</el-breadcrumb-item>
        </el-breadcrumb>
      </div>
    <div class="container ">

<!--      <h1 class="section-title text-left">{{services.find(x => x.name_slug === $route.path.split('/')[2]).name}}</h1>-->
    <div class="service-wrapper">
        <div class="service-left">
          <el-select class="service-select" v-model="service" placeholder="Услуги">
          <el-option
            v-for="item in services"
            :key="item.id"
            :label="item.name"
            :value="item.name_slug">
          </el-option>
        </el-select>
          <div @click="$router.push(`/services/${service.name_slug}`)" class="service-item" v-for="service in services" :key="service.id">
            <p>{{service.name}}</p>
          </div>
        </div>
        <div class="service-right">
            <div class="cars-wrapper">
<!--              <div @click="$router.push(`/cars/${car.category}/${car.name_slug}`)"-->
<!--                   class="car-item" v-for="car in cars" :key="car.id">-->
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
<!--                <div class="car-item__group">-->
<!--                  <el-button type="primary">Заказать</el-button>-->
<!--                  <el-button plain type="primary">Подробнее</el-button>-->

<!--                </div>-->
<!--              </div>-->
              <CarCard v-for="car in cars" :key="car.id" :car="car"/>
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

    try{
      const get_services = await $axios.get(`/api/get_services`)
      const get_cars = await $axios.get(`/api/get_cars_by_service?service_name_slug=${params.service_slug}`)
      const services = get_services.data
      const cars = get_cars.data
      return {services,cars}//,banners
    }catch (e) {
      const err = 404
      return {err}
    }
  },
    data:function(){
      return{
        service:null,
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
      this.service = this.$route.params.service_slug
    },
    watch:{
      service(val){
        console.log(val)
        this.$router.push(`/services/${val}`)
      }
    }
  }
</script>


