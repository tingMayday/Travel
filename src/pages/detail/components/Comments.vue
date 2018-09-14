<template>
    <div class="comments">
        <div class="comments_title">用户评论</div>
        <ul class="comments_list">
            <li 
                class="item"
                v-for="(item, index) of newList"
                :key="index">
                <div class="item_header">
                    <div class="stars" v-if="item.stars">
                        <span 
                            v-for="(star, idx) of item.stars" 
                            :key="idx"
                            class="iconfont">&#xe663;</span>
                    </div>
                    <div>
                        <span>{{item.user}}</span>
                        <span>{{item.date}}</span>
                    </div>
                </div>
                <div class="item_con">
                    {{item.content}}
                </div>
                <ul class="item_imgs">
                    <li class="item_img" v-for="(img, idx) of item.imgs" :key="idx">
                        <img :src="img" alt="">
                    </li>
                </ul>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'DetailComments',
    props: {
        list: Array
    },
    computed: {
        newList() {
            this.list.forEach(item => {
                let stars = [];
                for(let i=0; i < item.star; i++){
                    stars.push(i)
                }
                item.stars = stars
            })
            return this.list
        },
    }
}
</script>

<style lang="scss" scoped>
    .comments{
        padding: .2rem 0;
        background: #eee;
        .comments_title{
            position: relative;
            padding: .33rem .2rem .33rem .4rem;
            background: #fff;
            border-bottom: .02rem solid #eee;
            &::before{
                content: " ";
                position: absolute;
                top: .33rem;
                left: .2rem;
                width: .06rem;
                height: .25rem;
                background: #1ba9ba;
                border-radius: .04rem;
            }
        }
        .comments_list{
            padding: .2rem;
            background: #fff;
            .item{
                padding: .2rem 0;
                border-bottom: .02rem solid #eee;
                .item_header{
                    display: flex;
                    align-items: center;
                    justify-content: space-between;
                    .iconfont{
                        padding: 0 .03rem;
                        font-size: .24rem;
                        color: #ffb436;
                    }
                }
                .item_con{
                    padding: .2rem 0;
                }
                .item_imgs{
                    display: flex;
                    flex-wrap: wrap;
                    .item_img{
                        width: 33.33%;
                        padding: .05rem;
                        box-sizing: border-box;
                        img{
                            width: 100%;
                        }
                    }
                }
            }
        }
    }
</style>
