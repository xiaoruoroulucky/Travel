<template>
  <div>
      <div class="banner" @click="handleBannerClick">
        <img class="banner-img" :src="bannerImg">
        <div class="banner-info">
          <div class="banner-title">{{this.sightName}}</div>
          <div class="banner-number">
            <span class="iconfont banner-icon">&#xe61a;</span>
            {{this.bannerImgs.length}}
          </div>
        </div>
      </div>
    <fade-animation>
        <common-gallary :imgs="bannerImgs" v-show="showGallary" @close="handleGallaryClose"></common-gallary>
    </fade-animation>
  </div>
</template>

<script>
  import CommonGallary from 'common/gallary/Gallary'
  import FadeAnimation from 'common/fade/FadeAnimation'
    export default {
        name: "DetailBanner",
        components: {CommonGallary,FadeAnimation},
        props:{
          sightName:String,
          bannerImg:String,
          bannerImgs:Array
        },
        data:function () {
          return {
            showGallary:false
          }
        },
        methods:{
          handleBannerClick:function () {
            this.showGallary = true;
          },
          handleGallaryClose:function () {
            this.showGallary = false;
          }
        }
    }
</script>

<style lang="stylus" scoped>
  .banner
    position relative
    overflow hidden
    height 0
    padding-bottom 55%
    .banner-img
      width 100%
    .banner-info
      position absolute
      line-height .6rem
      display flex
      right 0
      bottom 0
      left 0
      color #ffffff
      background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
      .banner-title
        flex 1
        font-size .32rem
        padding 0 .2rem
      .banner-number
        line-height .32rem
        height .32rem
        margin-top .14rem
        padding 0 .4rem
        border-radius .2rem
        background rgba(0,0,0,.8)
        font-size .24rem
        .banner-icon
          font-size .24rem
</style>
