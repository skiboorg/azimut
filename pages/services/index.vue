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
        <h1 class="section-title">Наши услуги</h1>

        <div class="services">
          <div @click="$router.push(`/services/${service.name_slug}`)"  class="services-item" v-for="service in services" :key="service.id">
            <img rel="preload" :src="service.image" alt="">
            <p>{{service.name}}</p>
          </div>
        </div>
        <div @click="openModal" class="text-center"><el-button type="primary">Заказать авто</el-button></div>
      </div>

    </section>

  </div>

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


