<template>
   <div class="callback-form">
        <div class="callback-form__inner">
           <el-input v-model="name" placeholder="Ваше имя"></el-input>
        <el-input v-model="phone" placeholder="Ваш номер телефона"></el-input>
        <el-select v-model="service" placeholder="Вид услуги">
          <el-option
            v-for="item in services"
            :key="item.id"
            :label="item.name"
            :value="item.name">
          </el-option>
        </el-select>
        <el-input type="textarea" rows="5" resize="none" v-model="text" placeholder="Текст сообщения"></el-input>
           <el-checkbox class="mb-10" v-model="agree">Я согласен(а) на обработку персональных данных</el-checkbox>
          <el-button type="primary">Оставить заявку</el-button>

        </div>

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
  data() {
      return {
        dialogVisible:false,
        agree:false,
        phone:null,
        service:null,
        text:null,
        car_id:null,

      }
    },
  };
</script>