<template>
    <div class="header">
        <span>城市选择</span>
        <router-link to="/">
            <div class="iconfont">&#xe624;</div>
        </router-link>
    </div>
</template>

<script>
export default {
    name: 'CityHeader',
    
}
</script>

<style lang="scss" scoped>
    .header{
        position: relative;
        line-height: $headerHeight;
        font-size: .32rem;
        text-align: center;
        color: #fff;
        overflow: hidden;
        background: $bgColor;
        .iconfont{
            position: absolute;
            left: 0;
            top: 0;
            font-size: .36rem;
            color: #fff;
        }
    }
</style>
