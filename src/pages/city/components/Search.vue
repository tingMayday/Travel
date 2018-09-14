<template>
    <div>
        <div class="search">
            <input v-model="keyword"  class="search_input" type="text" placeholder="输入城市名或拼音" />
        </div>

        <div 
            class="search_content" 
            ref="search"
            v-show="keyword"
        >
            <ul>
                <li 
                    class="search_item"
                    v-for="item of list" 
                    :key="item.id"
                    @click="handleCityClick(item.name)"
                >
                    {{item.name}}
                </li>
                <li class="search_item" v-show="hasNoData">没有找到匹配项</li>
            </ul>
        </div>
        
    </div>
</template>

<script>
import Bscroll from 'better-scroll'
export default {
    name: 'CitySearch',
    props: {
        cities: Object
    },
    data() {
        return{
            keyword: '',
            list: [],
            timer: null
        }
    },
    computed: {
        hasNoData() {
            return !this.list.length
        }
    },
    watch: {
        keyword() {
            if(this.timer){
                clearTimeout(this.timer)
            }
            if(!this.keyword) {
                this.list = []
                return
            }
            this.timer = setTimeout(() => {
                const result = []
                for (let i in this.cities) {
                    this.cities[i].forEach((value) => {
                        if(value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
                            result.push(value)
                        }
                    })
                }
                this.list = result
            }, 100)
        }
    },
    mounted () {
        this.scroll = new Bscroll(this.$refs.search, {
            preventDefault: false
        })
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
    .search{
        padding: 0 .1rem;
        height: .72rem;
        background: $bgColor;
        .search_input{
            width: 100%;
            height: .62rem;
            padding: 0 .1rem;
            color: #666;
            line-height: .62rem;
            text-align: center;
            border-radius: .06rem;
            box-sizing: border-box;
        }
    }
    .search_content{
        position: absolute;
        top: 1.58rem;
        bottom: 0;
        left: 0;
        right: 0;
        background: #eee;
        overflow: hidden;
        z-index: 1;
        .search_item{
            padding: .3rem 0 .3rem .2rem;
            color: #666;
            background: #fff;
            border-bottom: .02rem solid #eee;
        }
    }
</style>
