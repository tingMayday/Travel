<template>
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title">当前城市</div>
                <div class="btn_list">
                    <div class="btn_wrapper">
                        <div class="btn">{{this.$store.state.city}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title">热门城市</div>
                <div class="btn_list">
                    <div 
                        class="btn_wrapper" 
                        v-for="item of hot" 
                        :key="item.id" 
                        @click="handleCityClick(item.name)"
                    >
                        <div class="btn">{{item.name}}</div>
                    </div>
                </div>
            </div>
            <div 
                class="area" 
                v-for="(item, key) of cities"
                :key="key"
                :ref="key"
            >
                <div class="title">{{key}}</div>
                <ul class="item_list">
                    <li 
                        class="item"
                        v-for="city of item"
                        :key="city.id"
                        @click="handleCityClick(city.name)"
                    >
                        {{city.name}}
                    </li>
                </ul>
            </div>
            
        </div>
    </div>
</template>

<script>
import Bscroll from 'better-scroll'

export default {
    name: 'CityList',
    props: {
        hot: Array,
        cities: Object,
        letter: String
    },
    mounted () {
        this.scroll = new Bscroll(this.$refs.wrapper, {
            preventDefault: false
        })
    },
    watch: {
        letter() {
            if(this.letter){
                const element = this.$refs[this.letter][0]
                this.scroll.scrollToElement(element)
            }
        }
    },
    methods: {
        handleCityClick(city){
            this.$store.commit('changeCity', city)
            this.$router.push('/')
        }
    }
}
</script>

<style lang="scss" scoped>
    .list{
        position: absolute;
        top: 1.58rem;
        bottom: 0;
        left: 0;
        right: 0;
        overflow: hidden;
        .title{
            line-height: .54rem;
            background: #eee;
            padding-left: .2rem;
            color: #666;
            font-size: .26rem;
        }
        .btn_list{
            display: flex;
            flex-wrap: wrap;
            padding: .1rem .6rem .1rem .1rem;
            .btn_wrapper{
                width: 33.33%;
                .btn{
                    padding: .1rem;
                    margin: .1rem;
                    text-align: center;
                    border: .02rem solid #ccc;
                    border-radius: .06rem;                
                }
            }
        }
        .item_list{
            .item{
                line-height: .76rem;
                color: $darkTextColor;
                padding-left: .2rem;
                border-bottom: .01rem solid #ccc;
            }
        }
    }
</style>
