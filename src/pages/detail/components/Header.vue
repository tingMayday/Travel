<template>
    <div>
        <router-link 
            tag="div" 
            to="/" 
            class="header_abs"
            v-show="showAbs">
            <span class="iconfont">&#xe624;</span>
        </router-link>
        <div class="header_fixed" v-show="!showAbs" :style="opacityStyle">
            <span>景点详情</span>
            <router-link to="/">
                <div class="iconfont">&#xe624;</div>
            </router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'DetailHeader',
    data() {
        return {
            showAbs: true,
            opacityStyle: {
                opactiy: 0
            }
        }
    },
     mounted () {
        window.addEventListener('scroll', this.handleScroll)
    },
    unmounted () {
        window.removeEventListener('scroll', this.handleScroll)
    },
    methods: {
        handleScroll() {
            const top = document.documentElement.scrollTop
            if(top > 60){
                let opacity = top / 140;
                opacity = opacity > 1 ? 1 : opacity;
                this.showAbs = false
                this.opacityStyle = {opacity}
            } else {
                this.showAbs = true
            }
        }
    }
}
</script>

<style lang="scss" scoped>
.header_abs{
    position: absolute;
    left: .2rem;
    top: .2rem;
    width: .8rem;
    height: .8rem;
    text-align: center;
    line-height: .8rem;
    background: rgba(0,0,0,.8);
    border-radius: .4rem;
    .iconfont{
        color: #fff;
        font-size: .4rem;
    }
}
.header_fixed{
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    line-height: $headerHeight;
    font-size: .32rem;
    text-align: center;
    color: #fff;
    background: $bgColor;
    z-index: 2;
    .iconfont{
        position: absolute;
        left: 0;
        top: 0;
        font-size: .36rem;
        color: #fff;
    }
}
</style>
