<template>
  <div class="header">
    <div class="header-left">
      <span class="iconfont">&#xe624;</span>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        <span class="city">{{this.$store.state.city}}</span>
        <span class="iconfont">&#xe62b;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  data () {
    return {
    }
  }
}
</script>

<style lang="scss" scoped>
  .header{
    display: flex;
    align-items: center;
    height: .86rem;
    padding: .12rem 0;
    background: $bgColor;
    color: #fff;
    box-sizing: border-box;
    .header-left{
      width: .64rem;
      padding: 0 0 0 .2rem;
    }
    .header-input{
      flex: 1;
      height: .62rem;
      padding-left: .1rem;
      line-height: .62rem;
      background: #fff;
      color: #ccc;
      border-radius: .1rem;
    }
    .header-right{
      display: flex;
      justify-content: center;
      width: 1.24rem;
      text-align: center;
      color: #fff;
      .city{
        display: inline-block;
        @include ellipsis()
      }
    }
  }
</style>
