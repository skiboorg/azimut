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
          <span v-html="feature.img"></span>
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
      <div class="callback-form">
        <div class="callback-form__inner">
           <el-input v-model="name" placeholder="Ваше имя"></el-input>
        <el-input v-model="phone" placeholder="Ваш номер телефона"></el-input>
        <el-select v-model="service" placeholder="Вид услуги">
          <el-option
            v-for="item in services"
            :key="item.id"
            :label="item.name"
            :value="item.id">
          </el-option>
        </el-select>
        <el-input type="textarea" rows="5" resize="none" v-model="input" placeholder="Текст сообщения"></el-input>
          <el-button type="primary">Оставить заявку</el-button>

        </div>

      </div>
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

  export default {
    components:{
            CarCard

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
              'с большим опытом работы',img:'<svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">\n' +
              '<path d="M20 18C17.7942 18 16 19.7942 16 22C16 24.2057 17.7942 26 20 26C22.2057 26 24 24.2057 24 22C24 19.7942 22.2057 18 20 18ZM20 24.6667C18.5296 24.6667 17.3333 23.4707 17.3333 22C17.3333 20.5293 18.5296 19.3333 20 19.3333C21.4704 19.3333 22.6667 20.5293 22.6667 22C22.6667 23.4707 21.4704 24.6667 20 24.6667Z" fill="url(#paint0_linear)"/>\n' +
              '<path d="M20 0C8.972 0 0 8.972 0 20C0 31.028 8.972 40 20 40C31.028 40 40 31.028 40 20C40 8.972 31.028 0 20 0ZM20 38.6667C9.707 38.6667 1.33333 30.293 1.33333 20C1.33333 9.707 9.707 1.33333 20 1.33333C30.293 1.33333 38.6667 9.707 38.6667 20C38.6667 30.293 30.293 38.6667 20 38.6667Z" fill="url(#paint1_linear)"/>\n' +
              '<path d="M20 4C11.1777 4 4 11.1778 4 20C4 28.8223 11.1777 36 20 36C28.8222 36 36 28.8223 36 20C36 11.1778 28.8222 4 20 4ZM20 5.33333C26.2321 5.33333 31.5651 9.24208 33.6857 14.7354L28.6908 16.4003C26.9776 16.9713 25.1254 16.8821 23.474 16.1477C21.2663 15.166 18.7334 15.166 16.5264 16.1477L16.2738 16.2598C14.7725 16.9278 13.0704 17.0625 11.4812 16.6387L6.13933 15.2142C8.12833 9.4705 13.5884 5.33333 20 5.33333ZM5.33333 20C5.33333 19.8642 5.33992 19.7299 5.34367 19.595L5.80667 19.7493C12.3797 21.9403 17.0281 27.6829 17.8549 34.5083C10.7811 33.4669 5.33333 27.3585 5.33333 20ZM20 34.6667C19.7352 34.6667 19.4723 34.6588 19.211 34.6448C18.4232 27.178 13.3882 20.8712 6.2285 18.485L5.44467 18.2238C5.51608 17.6354 5.62117 17.0575 5.76033 16.4926L11.1373 17.9265C11.858 18.1186 12.5979 18.2143 13.3372 18.2143C14.5286 18.2143 15.7171 17.9668 16.815 17.4786L17.0676 17.3666C18.9308 16.5372 21.0682 16.5378 22.9341 17.3673C24.8888 18.2351 27.0828 18.3418 29.1125 17.6648L34.1074 15.9998C34.3121 16.7203 34.4628 17.463 34.5552 18.2238L33.7713 18.485C26.6116 20.8712 21.5767 27.178 20.7888 34.6448C20.5277 34.6588 20.2647 34.6667 20 34.6667ZM22.1452 34.5083C22.972 27.6829 27.6203 21.9403 34.1934 19.7493L34.6564 19.595C34.6601 19.7299 34.6667 19.8642 34.6667 20C34.6667 27.3585 29.2189 33.4669 22.1452 34.5083Z" fill="url(#paint2_linear)"/>\n' +
              '<defs>\n' +
              '<linearGradient id="paint0_linear" x1="16" y1="21.9216" x2="24" y2="21.9216" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint1_linear" x1="1.79433e-07" y1="19.6078" x2="40" y2="19.6078" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint2_linear" x1="4" y1="19.6863" x2="36" y2="19.6863" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '</defs>\n' +
              '</svg>\n'},
          {id:2,text:'Автопарк оснащен современными моделями автомобилей от эконом до премиум-класса',img:'<svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">\n' +
              '<path d="M11.4231 26.0766L7.39973 22.0533C6.61137 21.2667 5.56637 20.8333 4.45309 20.8333H1.66637C1.20637 20.8333 0.833008 21.2067 0.833008 21.6667C0.833008 22.1267 1.20637 22.5 1.66637 22.5H4.45301C5.10965 22.5 5.75465 22.7666 6.21965 23.2316L8.82129 25.8332H1.66637C1.20637 25.8332 0.833008 26.2066 0.833008 26.6666C0.833008 27.1266 1.20637 27.5 1.66637 27.5H10.833C11.1696 27.5 11.473 27.2966 11.603 26.985C11.733 26.6733 11.6614 26.315 11.4231 26.0766Z" fill="url(#paint0_linear)"/>\n' +
              '<path d="M10.8337 30C10.3737 30 10.0003 30.3734 10.0003 30.8334V33.3334C10.0003 33.7934 9.62535 34.1668 9.16699 34.1668H4.16699C3.70863 34.1668 3.33363 33.7934 3.33363 33.3334V30C3.33363 29.54 2.96027 29.1667 2.50027 29.1667C2.04027 29.1667 1.66699 29.54 1.66699 30V33.3334C1.66699 34.7118 2.78863 35.8334 4.16699 35.8334H9.16699C10.5453 35.8334 11.667 34.7118 11.667 33.3334V30.8334C11.667 30.3734 11.2937 30 10.8337 30Z" fill="url(#paint1_linear)"/>\n' +
              '<path d="M36.2184 15.9284C33.9217 14.7267 28.7667 14.1667 20 14.1667C11.2333 14.1667 6.07836 14.7267 3.78164 15.9284C1.165 17.295 0 19.5784 0 23.3334C0 26.9434 0.826641 30.0834 0.861641 30.215C0.958281 30.58 1.28828 30.8334 1.66664 30.8334H8.97L12.1266 32.4118C12.2433 32.4701 12.3716 32.5001 12.5 32.5001H27.5C27.6284 32.5001 27.7566 32.4701 27.8716 32.4118L31.03 30.8334H38.3334C38.7117 30.8334 39.0417 30.58 39.1384 30.215C39.1734 30.0834 40 26.9434 40 23.3334C40 19.5784 38.835 17.295 36.2184 15.9284ZM37.675 29.1667H30.835C30.705 29.1667 30.5766 29.1967 30.4616 29.255L27.3033 30.8334H12.6966L9.54 29.255C9.42336 29.1967 9.295 29.1667 9.16664 29.1667H2.32664C2.095 28.105 1.66664 25.8117 1.66664 23.3333C1.66664 20.195 2.50328 18.4767 4.55164 17.405C6.54828 16.3616 11.745 15.8333 20 15.8333C28.255 15.8333 33.4516 16.3617 35.4484 17.405C37.4967 18.4766 38.3334 20.195 38.3334 23.3333C38.3334 25.8117 37.905 28.105 37.675 29.1667Z" fill="url(#paint2_linear)"/>\n' +
              '<path d="M38.3336 25.8333H31.1786L33.7786 23.2317C34.2452 22.7667 34.8886 22.5 35.547 22.5H38.3336C38.7936 22.5 39.167 22.1267 39.167 21.6667C39.167 21.2067 38.7936 20.8333 38.3336 20.8333H35.547C34.4336 20.8333 33.3886 21.2667 32.6003 22.0533L28.577 26.0767C28.3403 26.315 28.2686 26.6733 28.397 26.985C28.5253 27.2967 28.8303 27.5 29.167 27.5H38.3336C38.7936 27.5 39.167 27.1267 39.167 26.6667C39.1669 26.2066 38.7936 25.8333 38.3336 25.8333Z" fill="url(#paint3_linear)"/>\n' +
              '<path d="M29.9215 21.3133C29.7831 21.02 29.4898 20.8333 29.1665 20.8333H10.8332C10.5098 20.8333 10.2165 21.02 10.0782 21.3133C9.94153 21.605 9.98481 21.9517 10.1932 22.2L14.3598 27.2C14.5182 27.39 14.7532 27.5 14.9998 27.5H24.9998C25.2465 27.5 25.4815 27.39 25.6398 27.2L29.8065 22.2C30.0148 21.9516 30.0582 21.605 29.9215 21.3133ZM24.6082 25.8333H15.3898L12.6115 22.5H27.3865L24.6082 25.8333Z" fill="url(#paint4_linear)"/>\n' +
              '<path d="M36.5984 16.335C35.65 14.155 32.4767 6.96999 31.3734 6.03163C29.9984 4.86327 26.06 4.16663 20.8334 4.16663H19.1667C13.9401 4.16663 10.0017 4.86327 8.62674 6.02999C7.52338 6.96834 4.34838 14.1533 3.40174 16.3333C3.2201 16.7567 3.41338 17.2467 3.8351 17.43C4.2551 17.6133 4.74846 17.4216 4.93174 16.9983C6.81338 12.6667 9.1151 7.85334 9.70674 7.3017C10.3484 6.7567 13.0634 5.83334 19.1667 5.83334H20.8334C26.9367 5.83334 29.6517 6.7567 30.29 7.29834C30.885 7.85334 33.1867 12.665 35.0684 16.9983C35.205 17.3133 35.5134 17.5 35.8334 17.5C35.9434 17.5 36.0584 17.4783 36.165 17.4316C36.5867 17.2483 36.78 16.7566 36.5984 16.335Z" fill="url(#paint5_linear)"/>\n' +
              '<path d="M37.5003 29.1667C37.0403 29.1667 36.6669 29.54 36.6669 30V33.3334C36.6669 33.7934 36.2919 34.1668 35.8336 34.1668H30.8336C30.3752 34.1668 30.0002 33.7934 30.0002 33.3334V30.8334C30.0002 30.3734 29.6269 30 29.1669 30C28.7069 30 28.3335 30.3734 28.3335 30.8334V33.3334C28.3335 34.7118 29.4551 35.8334 30.8335 35.8334H35.8335C37.2119 35.8334 38.3335 34.7118 38.3335 33.3334V30C38.3337 29.54 37.9603 29.1667 37.5003 29.1667Z" fill="url(#paint6_linear)"/>\n' +
              '<defs>\n' +
              '<linearGradient id="paint0_linear" x1="0.833008" y1="24.1013" x2="11.6671" y2="24.1013" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint1_linear" x1="1.66699" y1="32.4347" x2="11.667" y2="32.4347" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint2_linear" x1="1.79433e-07" y1="23.1537" x2="40" y2="23.1537" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint3_linear" x1="28.334" y1="24.1013" x2="39.167" y2="24.1013" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint4_linear" x1="9.99951" y1="24.1013" x2="30.0001" y2="24.1013" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint5_linear" x1="3.3335" y1="10.7026" x2="36.6666" y2="10.7026" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint6_linear" x1="28.3335" y1="32.4347" x2="38.3335" y2="32.4347" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '</defs>\n' +
              '</svg>\n'},
          {id:3,text:'Услуги оказываются \n' +
              'в соответствии с требованиями безопасности',img:'<svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">\n' +
              '<g clip-path="url(#clip0)">\n' +
              '<path d="M36.7049 17.4433V5.84111C36.7049 5.52572 36.5017 5.24604 36.2017 5.1487L20.4692 0.0359673C20.3099 -0.0160632 20.1452 -0.00973515 19.9994 0.0432328C19.8523 -0.00926641 19.6881 -0.0155944 19.5288 0.0359673L3.7968 5.1487C3.49673 5.24596 3.29361 5.52518 3.29361 5.84111L3.29454 17.4157C3.28821 17.5849 2.84611 34.4148 19.623 39.9629C19.6968 39.9878 19.7746 40 19.852 40H20.1476C20.225 40 20.3028 39.9878 20.3765 39.9629C37.1529 34.4148 36.7108 17.5844 36.7049 17.4433ZM20.0294 38.5437H19.9696C4.35929 33.3111 4.72585 18.1158 4.74944 17.4433V6.3697L19.9783 1.42071C19.9855 1.41845 19.9923 1.41571 19.9995 1.41345C20.0058 1.41571 20.0131 1.41845 20.0199 1.42071L35.2491 6.37009L35.2501 17.4713C35.2559 17.6288 35.6682 33.2988 20.0294 38.5437Z" fill="url(#paint0_linear)"/>\n' +
              '<path d="M32.1609 7.91015L20.3546 3.93724C20.2524 3.90333 20.1464 3.89513 20.0482 3.90334C19.9496 3.89568 19.845 3.90333 19.7418 3.93724L7.93695 7.91007C7.6414 8.01007 7.44141 8.28749 7.44141 8.60022L7.44234 17.6405C7.44641 17.7704 8.03655 30.7026 19.7854 35.2538C19.87 35.2864 19.9596 35.3027 20.0482 35.3027C20.1369 35.3027 20.2265 35.2864 20.3111 35.2538C32.0604 30.7026 32.6514 17.7705 32.6563 17.6148V8.60022C32.656 8.28756 32.4564 8.01015 32.1609 7.91015ZM20.0482 33.793C9.46067 29.5034 8.90131 17.7089 8.89724 17.6152V9.12333L20.0482 5.37042L31.2006 9.12333L31.201 17.589C31.1961 17.7084 30.6358 29.5034 20.0482 33.793Z" fill="url(#paint1_linear)"/>\n' +
              '<path d="M28.3818 14.6235C28.0723 14.3647 27.6129 14.4081 27.3564 14.7158L18.9315 24.8066L13.497 19.0996C13.2178 18.8073 12.7585 18.7982 12.4679 19.0738C12.1765 19.3512 12.1652 19.8123 12.4422 20.1029L18.4396 26.4013C18.5777 26.5457 18.7682 26.6275 18.9673 26.6275C18.975 26.6275 18.9827 26.6275 18.9908 26.6266C19.1985 26.6203 19.3932 26.5248 19.5262 26.3659L28.4743 15.6484C28.7316 15.3399 28.6904 14.881 28.3818 14.6235Z" fill="url(#paint2_linear)"/>\n' +
              '</g>\n' +
              '<defs>\n' +
              '<linearGradient id="paint0_linear" x1="3.29248" y1="19.6079" x2="36.7069" y2="19.6079" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint1_linear" x1="7.44141" y1="19.2937" x2="32.6563" y2="19.2937" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint2_linear" x1="12.2417" y1="20.4215" x2="28.6432" y2="20.4215" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<clipPath id="clip0">\n' +
              '<rect width="40" height="40" fill="white"/>\n' +
              '</clipPath>\n' +
              '</defs>\n' +
              '</svg>\n'},
          {id:4,text:'Компания работает \n' +
              'на рынке более 8 лет',img:'<svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">\n' +
              '<path d="M38 8H29.3333V5.33333C29.3311 3.49316 27.8402 2.00228 26 2H14C12.1598 2.00228 10.6689 3.49316 10.6667 5.33333V8H2C0.895508 8 0 8.89551 0 10V24.8398C0.00423177 25.6855 0.537109 26.4378 1.33333 26.722V36C1.33333 37.1045 2.22884 38 3.33333 38H36.6667C37.7712 38 38.6667 37.1045 38.6667 36V26.7227C39.4629 26.4382 39.9961 25.6855 40 24.8398V10C40 8.89551 39.1045 8 38 8ZM12 5.33333C12 4.22884 12.8955 3.33333 14 3.33333H26C27.1045 3.33333 28 4.22884 28 5.33333V8H26.6667V5.33333C26.6667 4.96517 26.3682 4.66667 26 4.66667H14C13.6318 4.66667 13.3333 4.96517 13.3333 5.33333V8H12V5.33333ZM25.3333 8H14.6667V6H25.3333V8ZM37.3333 36C37.3333 36.3682 37.0348 36.6667 36.6667 36.6667H3.33333C2.96517 36.6667 2.66667 36.3682 2.66667 36V26.9512L17.3333 28.974V30.6667C17.3333 31.7712 18.2288 32.6667 19.3333 32.6667H20.6667C21.7712 32.6667 22.6667 31.7712 22.6667 30.6667V28.974L37.3333 26.9512V36ZM21.3333 30.6667C21.3333 31.0348 21.0348 31.3333 20.6667 31.3333H19.3333C18.9652 31.3333 18.6667 31.0348 18.6667 30.6667V26.6667C18.6667 26.2985 18.9652 26 19.3333 26H20.6667C21.0348 26 21.3333 26.2985 21.3333 26.6667V30.6667ZM38.6667 24.8398C38.667 25.1722 38.4225 25.4541 38.0934 25.5007L37.9085 25.526L22.6667 27.6279V26.6667C22.6667 25.5622 21.7712 24.6667 20.6667 24.6667H19.3333C18.2288 24.6667 17.3333 25.5622 17.3333 26.6667V27.6279L1.90723 25.5007C1.57812 25.4544 1.33301 25.1725 1.33333 24.8398V10C1.33333 9.63184 1.63184 9.33333 2 9.33333H38C38.3682 9.33333 38.6667 9.63184 38.6667 10V24.8398Z" fill="url(#paint0_linear)"/>\n' +
              '<defs>\n' +
              '<linearGradient id="paint0_linear" x1="1.79433e-07" y1="19.6471" x2="40" y2="19.6471" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '</defs>\n' +
              '</svg>\n'},
          {id:5,text:'Персональный подход к каждому клиенту',img:'<svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">\n' +
              '<g clip-path="url(#clip0)">\n' +
              '<path d="M23.9566 13.9844C24.3887 13.9844 24.7394 13.6343 24.7394 13.2031C24.7394 12.7719 24.3887 12.4219 23.9566 12.4219C23.5236 12.4219 23.1738 12.7719 23.1738 13.2031C23.1738 13.6343 23.5236 13.9844 23.9566 13.9844Z" fill="url(#paint0_linear)"/>\n' +
              '<path d="M16.129 13.9844C16.561 13.9844 16.9118 13.6343 16.9118 13.2031C16.9118 12.7719 16.561 12.4219 16.129 12.4219C15.696 12.4219 15.3462 12.7719 15.3462 13.2031C15.3462 13.6343 15.696 13.9844 16.129 13.9844Z" fill="url(#paint1_linear)"/>\n' +
              '<path d="M17.9502 19.3543C18.6073 19.6634 19.3115 19.8203 20.0426 19.8203C20.7578 19.8203 21.4482 19.6698 22.0949 19.3732C22.4879 19.1928 22.6597 18.729 22.4793 18.3368C22.2986 17.945 21.8338 17.7732 21.4409 17.9535C21.0009 18.1552 20.5303 18.2578 20.0426 18.2578C19.5439 18.2578 19.0644 18.1513 18.6177 17.941C18.2266 17.757 17.76 17.9242 17.5759 18.3145C17.3915 18.7049 17.5591 19.1703 17.9502 19.3543Z" fill="url(#paint2_linear)"/>\n' +
              '<path d="M37.3064 31.6227C37.3064 27.3267 32.4042 23.9576 28.2023 23.798L26.0585 21.8757C28.6695 19.9744 30.2543 16.919 30.2543 13.6719V8.51564C30.2543 3.77717 26.3793 -0.078125 21.6163 -0.078125H18.4851C13.7285 -0.078125 9.9021 3.76344 9.9021 8.51564V13.6719C9.9021 16.9135 11.4658 19.9631 14.0429 21.861L11.8829 23.798C7.69013 23.9573 2.77881 27.3179 2.77881 31.6227V39.1407C2.77881 39.5722 3.12922 39.922 3.56159 39.922H36.5236C36.956 39.922 37.3064 39.5722 37.3064 39.1407V31.6227ZM18.3087 34.7657H21.7722L22.5929 38.3594H17.4642L18.3087 34.7657ZM21.8395 33.2032H18.2592L17.6586 31.3358L20.0431 30.1459L22.4785 31.3618L21.8395 33.2032ZM20.0428 27.7985L17.3226 23.4556C18.206 23.7006 19.1239 23.8279 20.0507 23.8279C20.9686 23.8279 21.8798 23.703 22.7586 23.462L20.0428 27.7985ZM21.1631 28.9582L24.9214 22.9563L26.9483 24.7739L24.3691 30.5585L21.1631 28.9582ZM18.4851 1.48438H21.6163C25.5161 1.48438 28.6888 4.63838 28.6888 8.51564V9.16139L27.2189 7.04896C27.0859 6.85762 26.874 6.73555 26.6413 6.71602C26.4083 6.69649 26.1796 6.78163 26.0163 6.94826C24.4251 8.5724 22.5828 9.29689 20.0431 9.29689C17.5036 9.29689 15.661 8.5724 14.0686 6.94826C13.9047 6.78071 13.6738 6.69587 13.4405 6.71632C13.2069 6.73677 12.9947 6.86067 12.8626 7.05415L11.4677 9.09426V8.51564C11.4677 4.63838 14.6156 1.48438 18.4851 1.48438ZM11.4677 13.6719V11.8662L13.6417 8.68654C15.3834 10.1651 17.4415 10.8594 20.0431 10.8594C22.6473 10.8594 24.707 10.1636 26.449 8.68196L28.6888 11.901V13.6719C28.6888 18.3506 24.8571 22.2657 20.0507 22.2657C15.2599 22.2657 11.4677 18.3628 11.4677 13.6719ZM15.1638 22.9566L18.9227 28.9582L15.7161 30.5585L13.1369 24.7739L15.1638 22.9566ZM4.34437 31.6227C4.34437 28.4043 8.26438 25.6254 11.69 25.3727L14.6186 31.9404C14.7055 32.1351 14.8685 32.2861 15.0697 32.3582C15.2709 32.4302 15.4925 32.4167 15.684 32.3215L16.2417 32.0429L16.8768 34.0168L15.8561 38.3594H4.34437V31.6227ZM35.7408 38.3594H24.1985L23.2096 34.0287L23.8906 32.0664L24.4012 32.3215C24.5939 32.4177 24.8162 32.4296 25.0155 32.3582C25.2167 32.2861 25.3797 32.1351 25.4666 31.9404L28.3952 25.3727C31.8208 25.6257 35.7408 28.4043 35.7408 31.6227V38.3594Z" fill="url(#paint3_linear)"/>\n' +
              '<path d="M30.2196 34.7657H27.0884C26.6561 34.7657 26.3057 35.1154 26.3057 35.5469C26.3057 35.9785 26.6561 36.3282 27.0884 36.3282H30.2196C30.6519 36.3282 31.0023 35.9785 31.0023 35.5469C31.0023 35.1154 30.6519 34.7657 30.2196 34.7657Z" fill="url(#paint4_linear)"/>\n' +
              '<path d="M33.3072 34.7657C33.7393 34.7657 34.09 35.1157 34.09 35.5469C34.09 35.9782 33.7393 36.3282 33.3072 36.3282C32.8751 36.3282 32.5244 35.9782 32.5244 35.5469C32.5244 35.1157 32.8751 34.7657 33.3072 34.7657Z" fill="url(#paint5_linear)"/>\n' +
              '</g>\n' +
              '<defs>\n' +
              '<linearGradient id="paint0_linear" x1="23.1738" y1="13.1878" x2="24.7394" y2="13.1878" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint1_linear" x1="15.3462" y1="13.1878" x2="16.9118" y2="13.1878" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint2_linear" x1="17.501" y1="18.8241" x2="22.551" y2="18.8241" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint3_linear" x1="2.77881" y1="19.5298" x2="37.3064" y2="19.5298" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint4_linear" x1="26.3057" y1="35.5316" x2="31.0023" y2="35.5316" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<linearGradient id="paint5_linear" x1="32.5244" y1="35.5316" x2="34.09" y2="35.5316" gradientUnits="userSpaceOnUse">\n' +
              '<stop stop-color="#00BE91"/>\n' +
              '<stop offset="1" stop-color="#00B091"/>\n' +
              '</linearGradient>\n' +
              '<clipPath id="clip0">\n' +
              '<rect width="40" height="40" fill="white"/>\n' +
              '</clipPath>\n' +
              '</defs>\n' +
              '</svg>\n'},
        ],


        customers:[
          {id:1,img:'http://placehold.it/300'},
          {id:2,img:'http://placehold.it/300'},
          {id:3,img:'http://placehold.it/300'},
          {id:4,img:'http://placehold.it/300'},
          {id:5,img:'http://placehold.it/300'},
          {id:6,img:'http://placehold.it/300'},
        ]

      }
    },
  }
</script>


