<template>
  <div>
    <section>
      <div class="container">
        <el-breadcrumb separator="/">
          <el-breadcrumb-item :to="{ path: '/' }">Главная</el-breadcrumb-item>
          <el-breadcrumb-item>Ответы на часто задаваемые вопросы</el-breadcrumb-item>
        </el-breadcrumb>
      </div>
      <div class="container page-container">
        <h1 class="section-title">Ответы на часто задаваемые вопросы</h1>


          <el-collapse  v-for="q in faq" :key="q.id">
            <el-collapse-item :title="q.question" name="q.id">
              <div>{{q.answer}}</div>
             </el-collapse-item>
          </el-collapse>




      </div>

    </section>

  </div>

</template>

<script>
  export default {
    data:function(){
      return{

        faq:[
          {id:1,question:'Как арендовать автобус',answer:'ОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтвет'},
          {id:2,question:'Как арендовать автобус',answer:'ОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтвет'},
          {id:3,question:'Как арендовать автобус',answer:'ОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтвет'},
          {id:4,question:'Как арендовать автобус',answer:'ОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтвет'},
          {id:5,question:'Как арендовать автобус',answer:'ОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтвет'},
          {id:6,question:'Как арендовать автобус',answer:'ОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтвет'},
          {id:7,question:'Как арендовать автобус',answer:'ОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтветОтвет'},
        ]


      }
    },
  }
</script>


