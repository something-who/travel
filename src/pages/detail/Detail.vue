<template>
    <div>
        <detail-banner
            :sightName="sightName"
            :bannerImg="bannerImg"
            :bannerImgs="gallaryImgs"
        ></detail-banner>
    </div>
</template>
<script>
    import axios from "axios"
    import DetailBanner from './components/Banner'
    export default {
        name: "Detail",
        components:{
            DetailBanner
        },
        data (){
            return{
                sightName: "",
                bannerImg: "",
                gallaryImgs: [],
                categoryList: []
            }
        },
        methods : {
            getDetailInfo(){
                axios.get("/api/detail.json")
                    .then(this.HandlerDetailInfo)
            },
            HandlerDetailInfo(ret){
                ret = ret.data
                if(ret && ret.ret){
                    // console.log(ret.data)
                    const data = ret.data
                    this.sightName = data.sightName
                    this.bannerImg = data.bannerImg
                    this.gallaryImgs = data.gallaryImgs
                    this.categoryList = data.categoryList
                }
            }
        },
        mounted () {
            this.getDetailInfo()
        }
    }
</script>
<style media="screen" lang="stylus">
</style>