<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page, index) of pages" :key="index">
                <div 
                    class="icon" 
                    v-for="item of page" 
                    :key="item.id"
                >
                    <div class="icon_img">
                        <img :src="item.src" alt="item.keyword">
                    </div>
                    <p class="icon_desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
    
</template>

<script>
export default {
    name: 'HomeIcons',
    props: {
        iconList: {
            type: Array,
            default: []
        }
    },
    data() {
        return{
            swiperOption: {
                pagination: '.swiper-pagination',
                dynamicBullets: true
            }
        }
    },
    computed: {
        pages() {
            const pages = [];
            this.iconList.forEach((item, index) => {
                const page = Math.floor(index / 8)
                if(!pages[page]) {
                    pages[page] = []
                }
                pages[page].push(item)
            })
            return pages
        }
    }
}
</script>

<style lang="scss" scoped>
.icons{
    .swiper-slide{
        display: flex;
        flex-wrap: wrap;
        width: 100%;
        padding: .2rem 0 .5rem;
        overflow: hidden;
        .icon{
            width: 25%;
            text-align: center;
            color: $darkTextColor;
            overflow: hidden;
            box-sizing: border-box;
            .icon_img{
                position: relative;
                padding: 0 .35rem;
                box-sizing: border-box;
                img{
                    width: 100%;
                }
            }
            .icon_desc{
                padding: .1rem;
                @include ellipsis()
            }
        }
    }
}
</style>
