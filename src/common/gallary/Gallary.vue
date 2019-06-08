<template>
    <div class="container" @click="handleGallaryClick">
        <div class="wrapper">
          <swiper :options="swiperOptions">
            <swiper-slide v-for="(item,index) in imgs" :key="index">
              <img class="gallary_img" :src="item"/>
            </swiper-slide>

            <div class="swiper-pagination"  slot="pagination"></div>
          </swiper>
        </div>
    </div>
</template>

<script>
    export default {
        name: "CommonGallary",
        props:{
          imgs:{
              type:Array,
              default:function () {
                return []
              }
          }
        },
        data:function () {
          return {
            swiperOptions:{
              pagination:'.swiper-pagination',
              paginationType:'fraction',
              observeParents:true,
              observer:true
            }
          }
        },
        methods:{
          handleGallaryClick:function () {
            this.$emit('close');
          }
        }
    }
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow inherit
  .container
    z-index 99
    position fixed
    left 0
    right 0
    top 0
    bottom 0
    display flex
    flex-direction column
    justify-content center
    background-color #000
    .wrapper
      width 100%
      height 0
      padding-bottom 100%
      .gallary_img
        width 100%
      .swiper-pagination
        color #ffffff
        bottom -1rem
</style>
