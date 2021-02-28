<template>
  <div>

    <section>
      <div class="container">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item>Автопарк</el-breadcrumb-item>
        </el-breadcrumb>
      </div>

      <div class="container page-container">
        <h1 class="section-title">Автопарк</h1>
       <div class="categories ">
          <div @click="$router.push(`/cars/${cat.name_slug}`)"  class="services-item" v-for="cat in categories" :key="cat.id">
            <img style="object-fit: contain" :src="cat.image" alt="">
            <p class="text-center">{{cat.name}}</p>
          </div>
        </div>
<!--        <div class="text-center"><el-button type="primary">Заказать авто</el-button></div>-->
      </div>

    </section>

  </div>

</template>

<script>
  export default {
    async asyncData({$axios}){

    try{
      const get_categories = await $axios.get(`/api/get_categories`)
      const categories = get_categories.data
      console.log(categories)
      return {categories}//,banners
    }catch (e) {
      const err = 404
      return {err}
    }
  },
    data:function(){
      return{

        cars:[
          {id:1,img:'http://placehold.it/300',name_slug:'123',name:'Легковые машины'},
          {id:2,img:'http://placehold.it/300',name_slug:'123',name:'Микроавтобусы'},
          {id:3,img:'http://placehold.it/300',name_slug:'123',name:'Микроавтобусы2'},
          {id:4,img:'http://placehold.it/300',name_slug:'123',name:'Микроавтобусы5'},
        ],


      }
    },
  }
</script>


