<template>
  <div>
    <section>
      <div class="container">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item>Цены и оплата</el-breadcrumb-item>
        </el-breadcrumb>
      </div>
      <div class="container page-container">
        <h1 class="section-title">Цены и оплата</h1>
        <div class="page-wrapper">
          <div class="">
            <img src="/tseny_i_oplata.jpg" alt="">
          </div>
          <div class="">
             <p class="mb-40">

 Мы работаем как с юридическими, так и с физическими лицами, для этого предусмотрены разные варианты оплаты:<br><br>

- для физических лиц: наличный расчет;<br>
- для юридических лиц - безналичный расчет.<br><br>

Стоимость услуг рассчитываются индивидуально, исходя из конкретных потребностей заказчиков и планируемых программ.<br><br>

Минимальный заказ автотранспорта от 3х часов.<br><br>

Для юридических лиц предусмотрены индивидуальные условия оплаты и стоимости, которые обговариваются по телефону, либо при личной встрече.
        </p>

          </div>
        </div>






      </div>

    </section>
    <section class="callback">
      <div class="container">
        <div class="callback-wrapper">
          <div class="">
             <p>Заявка на аутсорсинг/аутстаффинг водителей</p>
          <p>Оставьте заявку — и мы поможем вам оптимизировать процесс работы</p>
          </div>
         <el-button  @click="openModal" type="primary">Заказать звонок</el-button>
        </div>
      </div>
    </section>
  </div>

</template>

<script>
  export default {
    data:function(){
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


