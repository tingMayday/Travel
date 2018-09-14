<template>
    <div>
        <div class="banner" @click="handleBannerClick">
            <img class="banner_img" :src="bannerImg" :alt="sightName">
            <div class="banner_info">
                <div class="banner_title">{{this.sightName}}</div>
                <div class="banner_num">
                    <span class="iconfont">&#xe63a;</span>
                    <span>{{this.gallaryImgs.length}}</span>
                </div>
            </div>
        </div>
        <fade-animation>
            <common-gallary 
                :imgs="gallaryImgs" 
                v-show="showGallary" 
                @close="handleGallaryClose"
            ></common-gallary>
        </fade-animation>
    </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary' 
import FadeAnimation from 'common/fade/FadeAnimation' 
export default {
    name: 'DetailBanner',
    components: {
        CommonGallary,
        FadeAnimation
    },
    props: {
        sightName: String,
        bannerImg: String,
        gallaryImgs: Array
    },
    data() {
        return {
            showGallary: false,
        }
    },
    methods: {
        handleBannerClick() {
            this.showGallary = true
        },
        handleGallaryClose() {
            this.showGallary = false
        }
    }
}
</script>

<style lang="scss" scoped>
    .banner{
        position: relative;
        height: 0;
        padding-bottom: 55%;
        overflow: hidden;
        .banner_img{
            width: 100%;
        }
        .banner_info{
            position: absolute;
            left: 0;
            right: 0;
            bottom: 0;
            display: flex;
            align-items: center;
            line-height: .6rem;
            color: #fff;
            background-image: linear-gradient(top, rgba(0,0,0,0), rgba(0,0,0,0.8));
            .banner_title{
                flex: 1;
                padding: 0 .2rem;
                font-size: .32rem;
                @include ellipsis();
            }
            .banner_num{
                height: .4rem;
                padding: 0 .32rem;
                line-height: .4rem;
                border-radius: .2rem;
                background: rgba(0,0,0,.5);
                font-size: .24rem;
                .iconfont{
                    font-size: .24rem;
                }
            }
        }
    }
</style>
