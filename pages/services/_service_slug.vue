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
      <h1 class="section-title text-left">Название услуги</h1>
    <div class="service-wrapper">
        <div class="service-left">
          <div @click="$router.push(`/services/${service.name_slug}`)" class="service-item" v-for="service in services" :key="service.id">
            <p>{{service.name}}</p>

          </div>
        </div>
        <div class="service-right">
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
      </div>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias animi cupiditate doloremque facilis libero magnam necessitatibus, perferendis quibusdam quidem saepe.</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias animi cupiditate doloremque facilis libero magnam necessitatibus, perferendis quibusdam quidem saepe.</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias animi cupiditate doloremque facilis libero magnam necessitatibus, perferendis quibusdam quidem saepe.</p>

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


