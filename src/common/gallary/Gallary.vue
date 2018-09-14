<template>
    <div class="gallary" @click="handleGallaryClcik">
        <div class="wrapper">
            <swiper :options="swiperOption">
                <swiper-slide v-for="(item, index) of imgs" :key="index">
                    <img class="gallary_img" :src="item" alt="">
                </swiper-slide>
                <div class="swiper-pagination" slot="pagination"></div>
            </swiper>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CommonGallary',
    props: {
        imgs: {
            type: Array,
            default: this.swiperList
        }
    },
    data() {
        return {
            swiperOption: {
                pagination: '.swiper-pagination',
                paginationType: 'fraction',
                observeParents: true,
                observer: true,
                loop: true
            }
        }
    },
    methods: {
        handleGallaryClcik() {
            this.$emit('close')
        }
    }
}
</script>

<style lang="scss" scoped>
    .gallary{
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        display: flex;
        flex-direction: column;
        justify-content: center;
        background: #000;
        z-index: 99;
        .wrapper{
            width: 100%;
            overflow: hidden;
            .gallary_img{
                width: 100%;
            }
            .swiper-pagination{
                position: fixed;
                bottom: 1rem;
                color: #fff;
            }
        }
    }
</style>
