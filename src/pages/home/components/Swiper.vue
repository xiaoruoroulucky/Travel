<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
      <!-- slides -->
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper_img" :src="item.imgUrl"/>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
    export default {
        name: "HomeSwiper",
        props:{
          list:Array
        },
        data:function () {
          return{
            swiperOption:{
              pagination:".swiper-pagination",
              loop:true,
              autoplay:{
                delay:10000
              },
              speed:1000
            },
          }
        },
        computed:{
          showSwiper:function () {
              return this.list.length
          }
        }
    }
</script>

<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background: #ffffff
  .wrapper
    overflow :hidden
    width: 100%
    height: 0
    padding-bottom :31.3%
    .swiper_img
      width:100%
</style>
