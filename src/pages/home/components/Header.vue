<template>
    <div class="header">
      <div class="header-left">
        <div class="iconfont back-icon">&#xe624;</div>
      </div>
      <div class="header-input">
        <span class="iconfont">&#xe632;</span>
        输入城市/景点/游玩主题
      </div>
      <router-link to="/city">
        <div class="header-right">
          <!--{{ this.$store.state.city}}-->
          {{this.city}}
          <span class="iconfont arrow-icon">&#xe600;</span>
        </div>
      </router-link>
    </div>
</template>

<script>
  import { mapState } from 'vuex'
    export default {
        name: "HomeHeader",
        computed:{
          ...mapState(['city'])
        }
    }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .header
    line-height:$headerHeight
    display:flex
    background :$bgColor
    color:#ffffff
    .header-left
      width:.64rem
      float :left
      .back-icon
        text-align:center
        font-size :.4rem
    .header-input
      flex :1
      background :#ffffff
      -webkit-border-radius: .1rem
      -moz-border-radius: .1rem
      border-radius: .1rem
      margin-top :.12rem
      margin-left :.2rem
      height :0.64rem
      color: #cccccc
      line-height .64rem
      padding-left :.2rem
    .header-right
      min-width :1.04rem
      padding 0 .1rem
      float:right
      text-align :center
      color:#ffffff
      .arrow-icon
        font-size :0.24rem
        margin-left: -.04rem
</style>
