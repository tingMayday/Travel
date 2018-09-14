<template>
<div class="wrapper">
    <swiper :options="swiperOption" v-if="showSwiper">
        <swiper-slide v-for="item of swiperList" :key="item.id">
            <img class="swiper_img" :src="item.imgUrl" alt="swiper">
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
</div>
</template>


<script>
export default {
    name: 'HomeSwiper',
    props: {
        swiperList: {
            type: Array,
            default: []
        }
    },
    data() {
        return {
            swiperOption: {
                pagination: '.swiper-pagination',
                loop: true
            }
        }
    },
    computed: {
        showSwiper () {
            return this.swiperList.length
        }
    }
}
</script>

<style lang="scss" scoped>
.wrapper{
    width: 100%;
    height: 0;
    padding-bottom: 37%;
    background: #eee;
    overflow: hidden;
    .swiper_img{
        width: 100%;
    }
}
</style>
