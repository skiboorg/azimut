<template>
  <div>
    <div class="car-item">
    <img :src="car.images[0].image" alt="">
    <p class="car-item__name">{{car.name}}</p>
    <div class="car-item__group">
      <p>от {{car.min_hour}} ч.</p>
      <p>Мест: {{car.seats}}</p>
    </div>
    <div class="car-item__group">
      <p v-if="car.price_km" class="text-bold">{{car.price_km}}р/км</p>
      <p v-if="car.price_hour"  class="text-bold">{{car.price_hour}}р/час</p>
    </div>
    <div class="car-item__group">
      <el-button @click="openModal" type="primary">Заказать</el-button>
      <nuxt-link :to="`/cars/${car.cat_slug}/${car.name_slug}`" >
        <el-button plain type="primary">Подробнее</el-button>
      </nuxt-link>

    </div>
  </div>

  </div>

</template>

<script>

export default {
  props:['car'],
  methods:{
    openModal(){
      document.getElementById('callbackModal').click()

    }
  }
};
</script>
