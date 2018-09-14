<template>
    <div>
        <div class="title">热门推荐</div>
        <ul>
            <router-link 
                tag="li"
                class="item" 
                v-for="item of recommendList" 
                :key="item.id" 
                :to="'/detail/' + item.id" >
                <img class="item_img" :src="item.imgUrl" :alt="item.title">
                <div class="item_info">
                    <p class="item_title">{{item.title}}</p>
                    <p class="item_desc">{{item.desc}}</p>
                    <button class="item_btn">查看详情</button>
                </div>

            </router-link>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'HomeRecommend',
    props: {
        recommendList: {
            type: Array,
            default: []
        }
    },
    data() {
        return{}
    }
}
</script>

<style lang="scss" scoped>
    .title{
        margin-bottom: .1rem;
        line-height: .8rem;
        text-indent: .2rem;
        border-bottom: .01rem solid #eee;
    }
    .item{
        display: flex;
        align-items: center;
        height: 1.9rem; 
        border-bottom: 1px solid #e0e0e0; 
        overflow: hidden;  
        .item_img{
            width: 1.7rem;
            height: 1.7rem;
            padding: .1rem;
        }
        .item_info{
            flex: 1;
            padding: .1rem;
            min-width: 0;
            .item_title{
                line-height: .4rem;
                font-size: .32rem;
                @include ellipsis();
            }
            .item_desc{
                line-height: .4rem;
                color: #ccc;
                @include ellipsis();
            }
            .item_btn{
                margin-top: .16rem;
                padding: 0 .2rem;
                line-height: .45rem;
                background: #ff9300;
                color: #fff;
                border-radius: .06rem;
            }
        }
    }
</style>
