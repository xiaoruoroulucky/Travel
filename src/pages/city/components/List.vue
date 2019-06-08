<template>
    <div class="list" ref="wrapper">
      <div>

        <div class="area">
          <div class="title border-topbottom">当前城市</div>
          <div class="button-list">
            <div class="button-wrapper">
              <div class="button">
                <!--{{this.$store.state.city}}-->
                {{this.currentCity}}
              </div>
            </div>
          </div>
        </div>

        <div class="area">
          <div class="title border-topbottom">热门城市</div>
          <div class="button-list">
            <div class="button-wrapper" v-for="item of hot" :key="item.id" @click="handleCityClick(item.name)">
              <div class="button">{{item.name}}</div>
            </div>
          </div>
        </div>

        <div class="area" v-for="(cityItem,key) of cities" :key="key" :ref="key">
          <div class="title border-topbottom">{{key}}</div>
          <div class="item-list" v-for="item of cityItem" :key="item.id">
            <div class="item border-bottom" @click="handleCityClick(item.name)">{{item.name}}</div>
          </div>
        </div>

      </div>
    </div>
</template>

<script>
    import { mapState,mapMutations } from 'vuex'
    import Bscroll from 'better-scroll'
    export default {
        name: "CityList",
        computed:{
          ...mapState({
            currentCity:'city'
          })
        },
        props:{
          cities:Object,
          hot:Array,
          letter:String
        },
        mounted:function () {
          this.scroll = new Bscroll(this.$refs.wrapper,{mouseWheel: true,click:true,tap:true});
        },
        methods:{
          handleCityClick:function (city) {
            // this.$store.commit('changeCity',city);
            this.changeCity(city);
            this.$router.push('/');
          },
          ...mapMutations(['changeCity'])
        },
        watch:{
          letter:function () {
            if(this.letter){
              const element = this.$refs[this.letter][0];
              this.scroll.scrollToElement(element);
            }
          }
        }
    }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
    .border-topbottom
      &:before
        border-color #ccc
      &:after
        border-color #ccc
    .border-bottom
      &:before
        border-color #ccc
    .list
      overflow hidden
      position absolute
      left 0
      top 1.58rem
      bottom 0
      right 0
      .title
        line-height .54rem
        background #eee
        padding-left .2rem
        color #666
        font-size .26rem
      .button-list
        overflow hidden
        padding .1rem .6rem .1rem .1rem
        .button-wrapper
          float left
          width 33.33%
          .button
            padding .1rem 0
            text-align center
            margin .1rem
            border .02rem solid #ccc
            border-radius .06rem
      .item-list
        cursor pointer
        .item
          line-height .76rem
          padding-left .2rem
          cursor pointer

</style>
