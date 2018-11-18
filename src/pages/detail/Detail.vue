<template>
    <div>
        <detail-banner
            :sightName="sightName"
            :bannerImg="bannerImg"
            :bannerImgs="gallaryImgs"
        ></detail-banner>
        <detail-header></detail-header>
        <div class="content">
            <detail-list :list="list"></detail-list>
        </div>
    </div>
</template>
<script>
    import axios from "axios"
    import DetailBanner from './components/Banner'
    import DetailHeader from './components/Header'
    import DetailList from './components/List'
    export default {
        name: "Detail",
        components:{
            DetailBanner,
            DetailHeader,
            DetailList
        },
        data (){
            return{
                sightName: "",
                bannerImg: "",
                gallaryImgs: [],
                list: []
            }
        },
        methods : {
            getDetailInfo(){
                axios.get("/api/detail.json",{
                    params: {
                        id: this.$route.params.id
                    }
                }
                )
                    .then(this.HandlerDetailInfo)
                // axios.get("/api/detail.json?id=" + this.$route.params.id)
            },
            HandlerDetailInfo(ret){
                ret = ret.data
                if(ret && ret.ret){
                    // console.log(ret.data)
                    const data = ret.data
                    this.sightName = data.sightName
                    this.bannerImg = data.bannerImg
                    this.gallaryImgs = data.gallaryImgs
                    this.list = data.categoryList
                }
            }
        },
        mounted () {
            this.getDetailInfo()
        }
    }
</script>
<style media="screen" lang="stylus">
    .content
        height 50rem
</style>