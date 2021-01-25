<template>
  <div>
    <section>
      <div class="container">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item>Контакты</el-breadcrumb-item>
        </el-breadcrumb>
      </div>
      <div class="container page-container">
        <h1 class="section-title">Контакты</h1>
        <p class="text-center">Офис Группы Компаний «Экспресс»</p>
        <div class="contact-map">
          <div class="contact-map__inner">
            <div class="contact-map__item">
              <p> ООО «АЗИМУТ»<br>
Директор Галичин Илья Олегович<br>
ИНН / КПП 7448145354 / 744801001</p>

            </div>
            <div class="contact-map__item">
              <img src="/map1.png" alt="">
              <p>Адрес: 454106, г. Челябинск,<br>ул. Косарева, д. 75</p>
            </div>
            <div class="contact-map__item">
            <img src="/map2.png" alt="">

              <p><a href="mailto:avto@gcexpress.ru">avto@gcexpress.ru</a></p>
            </div>
            <div class="contact-map__item">
             <img src="/map3.png" alt="">

              <p>+7 (982) 363-03-03<br>+7 (351) 225-10-65</p>
            </div>
            <div class="contact-map__item">
              <img src="/map4.png" alt="">

              <p>Время работы:<br>с 09:00 до 18:00</p>
            </div>
          </div>
          <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2278.227463941138!2d61.37208531624967!3d55.179290980403856!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x43c592d48e655e33%3A0x747d60b7c515e70f!2z0YPQuy4g0JrQvtGB0LDRgNC10LLQsCwgNzUsINCn0LXQu9GP0LHQuNC90YHQuiwg0KfQtdC70Y_QsdC40L3RgdC60LDRjyDQvtCx0LsuLCA0NTQxMDY!5e0!3m2!1sru!2sru!4v1609072113807!5m2!1sru!2sru" width="100%" height="550" frameborder="0" style="border:0;" allowfullscreen="" aria-hidden="false" tabindex="0"></iframe>

        </div>
        <p class="text-center">Ваш вопрос</p>
          <Form/>
      </div>

    </section>


  </div>

</template>

<script>
import Form from '@/components/Form';
  export default {
    components:{
            Form

        },
    data:function(){
      return{




      }
    },
  }
</script>


