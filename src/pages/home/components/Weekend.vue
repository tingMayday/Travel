<template>
    <div>
        <div class="title">周末去哪儿</div>
        <ul>
            <li 
                class="item" 
                v-for="item of weekendList" 
                :key="item.id"
            >
                <div class="item_img_wrapper">
                    <img class="item_img" :src="item.imgUrl" :alt="item.title">
                </div>
                <div class="item_info">
                    <p class="item_title">{{item.title}}</p>
                    <p class="item_desc">{{item.desc}}</p>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'HomeWeekend',
    props: {
        weekendList: {
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
        line-height: .8rem;
        background: #eee;
        text-indent: .2rem;
    }
    .item{ 
        .item_img_wrapper{
            .item_img{
                width: 100%;
            }
        }
        .item_info{
            padding: .1rem;
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
        }
    }
</style>
