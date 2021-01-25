<template>
  <div>
    <section class="banner">
      <client-only>
        <swiper class="banner_wrapper"  :options="swiperOption">
          <swiper-slide :style="'background: '+ banner.bg_color "  v-for="banner in banners"
                        :key="banner.id">
            <div class="banner-wrapper">
              <h3> {{banner.text}}</h3>
              <div class="">
                <img :src="banner.img" alt="">
              </div>
            </div>
          </swiper-slide>
          <div class="swiper-pagination banner-pagination" slot="pagination"></div>
        </swiper>
      </client-only>
    </section>
    <div class="container">
      <div class="features">
        <div class="features-item" v-for="feature in features" :key="feature.id">
          <img :src="feature.img" alt="">
          <p>{{feature.text}}</p>
        </div>
      </div>
    </div>
    <section>
      <div class="container">
        <h3 class="section-title">Наши услуги</h3>
        <div class="services services-desktop">
          <div @click="$router.push(`/services/${service.name_slug}`)" class="services-item" v-for="service in services" :key="service.id">
            <img :src="service.image" alt="">
            <p>{{service.name}}</p>
          </div>
        </div>
        <client-only>
          <swiper  class="banner_wrapper services-mobile"  :options="swiperOption">
            <swiper-slide v-if="service.show_at_index" v-for="service in services" :key="service.id">
              <div class="services-item">
                <img :src="service.image" alt="">
                <p>{{service.name}}</p>
              </div>
            </swiper-slide>
            <div class="swiper-button-prev" slot="button-prev"><svg width="26" height="14" viewBox="0 0 26 14" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M0.297882 6.28114C0.298187 6.28084 0.298441 6.28048 0.298798 6.28018L5.60564 0.998932C6.00321 0.603296 6.64625 0.604768 7.04199 1.00239C7.43768 1.39995 7.43615 2.04299 7.03859 2.43868L3.47557 5.98443H24.9844C25.5453 5.98443 26 6.43912 26 7.00005C26 7.56098 25.5453 8.01567 24.9844 8.01567H3.47562L7.03854 11.5614C7.4361 11.9571 7.43762 12.6001 7.04194 12.9977C6.6462 13.3954 6.00311 13.3968 5.60559 13.0012L0.298746 7.71992C0.298441 7.71962 0.298187 7.71926 0.297832 7.71896C-0.0999374 7.32195 -0.0986691 6.67683 0.297882 6.28114Z" fill="url(#paint0_linear)"/>
              <defs>
                <linearGradient id="paint0_linear" x1="26" y1="6.87658" x2="-1.15607e-05" y2="6.87658" gradientUnits="userSpaceOnUse">
                  <stop stop-color="#00BE91"/>
                  <stop offset="1" stop-color="#00B091"/>
                </linearGradient>
              </defs>
            </svg>
            </div>
            <div class="swiper-button-next" slot="button-next"><svg width="26" height="14" viewBox="0 0 26 14" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M25.7021 6.28114C25.7018 6.28084 25.7016 6.28048 25.7012 6.28018L20.3944 0.998932C19.9968 0.603296 19.3538 0.604768 18.958 1.00239C18.5623 1.39995 18.5638 2.04299 18.9614 2.43868L22.5244 5.98443H1.01562C0.454695 5.98443 0 6.43912 0 7.00005C0 7.56098 0.454695 8.01567 1.01562 8.01567H22.5244L18.9615 11.5614C18.5639 11.9571 18.5624 12.6001 18.9581 12.9977C19.3538 13.3954 19.9969 13.3968 20.3944 13.0012L25.7013 7.71992C25.7016 7.71962 25.7018 7.71926 25.7022 7.71896C26.0999 7.32195 26.0987 6.67683 25.7021 6.28114Z" fill="url(#paint0_linear)"/>
              <defs>
                <linearGradient id="paint0_linear" x1="1.16631e-07" y1="6.87658" x2="26" y2="6.87658" gradientUnits="userSpaceOnUse">
                  <stop stop-color="#00BE91"/>
                  <stop offset="1" stop-color="#00B091"/>
                </linearGradient>
              </defs>
            </svg>
            </div>
            <div class="swiper-pagination banner-pagination" slot="pagination"></div>
          </swiper>
        </client-only>
        <div class="text-center">
          <nuxt-link to="/services">
            <el-button type="primary">Все услуги</el-button>
          </nuxt-link>

        </div>
      </div>
    </section>
    <section>
      <div class="container">
        <h3 class="section-title">Популярные авто</h3>
         <client-only>
          <swiper class="cars_wrapper"  :options="carSwiperOption">
            <swiper-slide  v-for="car in cars" :key="car.id">
              <CarCard :car="car"/>
            </swiper-slide>
            <div class="car-swiper-button-prev swiper-button-prev" slot="button-prev"><svg width="26" height="14" viewBox="0 0 26 14" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M0.297882 6.28114C0.298187 6.28084 0.298441 6.28048 0.298798 6.28018L5.60564 0.998932C6.00321 0.603296 6.64625 0.604768 7.04199 1.00239C7.43768 1.39995 7.43615 2.04299 7.03859 2.43868L3.47557 5.98443H24.9844C25.5453 5.98443 26 6.43912 26 7.00005C26 7.56098 25.5453 8.01567 24.9844 8.01567H3.47562L7.03854 11.5614C7.4361 11.9571 7.43762 12.6001 7.04194 12.9977C6.6462 13.3954 6.00311 13.3968 5.60559 13.0012L0.298746 7.71992C0.298441 7.71962 0.298187 7.71926 0.297832 7.71896C-0.0999374 7.32195 -0.0986691 6.67683 0.297882 6.28114Z" fill="url(#paint0_linear)"/>
              <defs>
                <linearGradient id="paint0_linear" x1="26" y1="6.87658" x2="-1.15607e-05" y2="6.87658" gradientUnits="userSpaceOnUse">
                  <stop stop-color="#00BE91"/>
                  <stop offset="1" stop-color="#00B091"/>
                </linearGradient>
              </defs>
            </svg>
            </div>
            <div class="car-swiper-button-next swiper-button-next" slot="button-next"><svg width="26" height="14" viewBox="0 0 26 14" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M25.7021 6.28114C25.7018 6.28084 25.7016 6.28048 25.7012 6.28018L20.3944 0.998932C19.9968 0.603296 19.3538 0.604768 18.958 1.00239C18.5623 1.39995 18.5638 2.04299 18.9614 2.43868L22.5244 5.98443H1.01562C0.454695 5.98443 0 6.43912 0 7.00005C0 7.56098 0.454695 8.01567 1.01562 8.01567H22.5244L18.9615 11.5614C18.5639 11.9571 18.5624 12.6001 18.9581 12.9977C19.3538 13.3954 19.9969 13.3968 20.3944 13.0012L25.7013 7.71992C25.7016 7.71962 25.7018 7.71926 25.7022 7.71896C26.0999 7.32195 26.0987 6.67683 25.7021 6.28114Z" fill="url(#paint0_linear)"/>
              <defs>
                <linearGradient id="paint0_linear" x1="1.16631e-07" y1="6.87658" x2="26" y2="6.87658" gradientUnits="userSpaceOnUse">
                  <stop stop-color="#00BE91"/>
                  <stop offset="1" stop-color="#00B091"/>
                </linearGradient>
              </defs>
            </svg>
            </div>

          </swiper>
        </client-only>
      </div>
    </section>
    <section class="cb">
      <h3 class="section-title">Оставьте заявку на услугу</h3>
     <Form/>
    </section>
    <section>
      <h3 class="section-title">Наши постоянные заказчики</h3>
      <div class="container">
        <div class="customers">
          <div class="customers-item" v-for="customer in customers" :key="customer.id">
            <img :src="customer.img" alt="">
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
 import CarCard from '@/components/CarCard';
import Form from '@/components/Form';
  export default {
    components:{
            CarCard,
      Form

        },
    async asyncData({$axios}){

    try{
      //const get_banners = await $axios.get(`/api/get_streamers`)
      const get_services = await $axios.get(`/api/get_services`)
      const get_cars = await $axios.get(`/api/get_index_cars`)

      //const banners = get_streamers.data
      const services = get_services.data
      const cars = get_cars.data
      console.log(cars)
      return {services,cars}//,banners
    }catch (e) {
      const err = 404
      return {err}
    }
  },
    data:function(){
      return{
        name:null,
        phone:null,
        service:null,
        swiperOption: {
          slidesPerView: 1,
          //spaceBetween: 20,
          centeredSlides: true,


          autoplay:true,
          pagination: {
            el: '.swiper-pagination',
            dynamicBullets: true
          },
          navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev'
          }
          // breakpoints: {
          //   // when window width is >= 320px
          //   320: {
          //     centeredSlides: true,
          //     slidesPerView: 1,
          //     spaceBetween: 20
          //   },
          //   // when window width is >= 480px
          //   480: {
          //     slidesPerView: 1,
          //     spaceBetween: 30
          //   },
          //   // when window width is >= 640px
          //   640: {
          //     slidesPerView: 5,
          //     spaceBetween: 40
          //   }
          // }
        },
        carSwiperOption: {
          //slidesPerView: 4,
          spaceBetween: 0,
          //centeredSlides: true,

          navigation: {
            nextEl: '.car-swiper-button-next',
            prevEl: '.car-swiper-button-prev'
          },
          breakpoints: {
            // when window width is >= 320px
            320: {
              centeredSlides: true,
              slidesPerView: 1,
              spaceBetween: 20
            },
            // when window width is >= 480px
            480: {
              centeredSlides:true,
              slidesPerView: 1,
              spaceBetween: 30
            },
            // when window width is >= 640px
            640: {
              slidesPerView: 3,
              spaceBetween: 0
            },
             890: {
              slidesPerView: 4,
              spaceBetween: 0
            }
          }
        },
        banners:[
          {id:1,bg_color:'linear-gradient(90deg, #00BE91 0%, #00B091 100%)',text:'Аренда автомобилей. Аутсорсинг и аутстаффинг водителей',img:'/banner1.png'},
          {id:2,bg_color:'linear-gradient(90deg, #f0BE91 0%, #20B091 100%)',text:'Аренда автомобилей. Аутсорсинг и аутстаффинг водителей',img:'/banner1.png'},
          {id:3,bg_color:'linear-gradient(90deg, #40BE91 0%, #f0B091 100%)',text:'Аренда автомобилей. Аутсорсинг и аутстаффинг водителей',img:'/banner1.png'},
          {id:4,bg_color:'linear-gradient(90deg, #70BE91 0%, #90B091 100%)',text:'Аренда автомобилей. Аутсорсинг и аутстаффинг водителей',img:'/banner1.png'}
        ],
        features:[
          {id:1,text:'В компании работают специалисты и водители \n' +
              'с большим опытом работы',img:'/f1.png'},
          {id:2,text:'Автопарк оснащен современными моделями автомобилей от эконом до премиум-класса',img:'/f2.png'},
          {id:3,text:'Услуги оказываются \n' +
              'в соответствии с требованиями безопасности',img:'/f3.png'},
          {id:4,text:'Компания работает \n' +
              'на рынке более 8 лет',img:'/f4.png'},
          {id:5,text:'Персональный подход к каждому клиенту',img:'/f5.png'},
        ],


        customers:[
          {id:1,img:'/chelyabremont.jpg'},
          {id:2,img:'/fortum.jpg'},
          {id:3,img:'/tsement.jpg'},
          {id:4,img:'/vetropark.jpg'},

        ]

      }
    },
  }
</script>


