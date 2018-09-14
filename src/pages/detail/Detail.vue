<template>
    <div>
        <detail-banner 
            :sightName="sightName" 
            :bannerImg="bannerImg"
            :gallaryImgs="gallaryImgs"
        ></detail-banner>
        <detail-header></detail-header>
        <detail-list :list="categoryList"></detail-list>
        <detail-comments :list="comments"></detail-comments>
    </div>
</template>

<script>
    import axios from 'axios'
    import DetailBanner from './components/Banner'
    import DetailHeader from './components/Header'
    import DetailList from './components/List'
    import DetailComments from './components/Comments'
    export default {
        name: 'Detail',
        components: {
            DetailBanner,
            DetailHeader,
            DetailList,
            DetailComments
        },
        data(){
            return {
                sightName: '',
                bannerImg: '',
                gallaryImgs: [],
                categoryList: [],
                comments: []
            }
        },
        mounted() {
            this.getDetailInfo()
        },
        
        methods: {
            getDetailInfo() {
                axios.get('/api/detail.json', {
                    params: {
                        id: this.$route.params.id
                    }
                }).then(this.handleGetDataSucc)
            },
            handleGetDataSucc(res) {
                res = res.data
                if(res.ret && res.data) {
                    const data = res.data;
                    this.sightName = data.sightName
                    this.bannerImg = data.bannerImg
                    this.gallaryImgs = data.gallaryImgs
                    this.categoryList = data.categoryList
                    this.comments = data.comments
                }
            }
        }
    }
</script>
 
<style lang="scss" scoped>
.content{
    height: 50rem;
}
</style>
