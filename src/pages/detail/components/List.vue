<template>
    <div>
        <div 
            class="item" 
            v-for="(item, index) of list"
            :key="index">
            <div class="item_title">
                <span class="item_title_icon"></span>
                <span>{{item.title}}</span>
            </div>

            <div v-if="item.children" class="item_children">
                <detail-list :list="item.children"></detail-list>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'DetailList',
    props: {
        list: Array
    },
    data() {
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
    .item{
        .item_title{
            display: flex;
            align-items: center;
            line-height: .8rem;
            font-size: .32rem;
            padding: 0 .2rem;
            border-bottom: .02rem solid #eee;
            .item_title_icon{
                display: inline-block;
                width: .36rem;
                height: .36rem;
                background: url(//s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.9rem no-repeat;
                margin-right: .1rem;
                background-size: .4rem 3rem;
            }
        }
        .item_children{
            padding: 0 .2rem;
        }
    }
</style>
