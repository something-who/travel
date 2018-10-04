<template lang="html">
    <swiper
    :options="swiperOption" ref="mySwiper"
    class="wrapper"
    >
       <!-- slides -->
       <swiper-slide
       v-for="item of swiperList"
       :key="item.id">
           <img :src="item.imgUrl" alt="swiper">
       </swiper-slide>
       <!-- Optional controls -->
       <div class="swiper-pagination"  slot="pagination"></div>
   </swiper>
</template>

<script>
export default {
    name: 'HomeSwiper',
    data(){
        return{
            swiperOption:{
                loop: true,
                pagination: '.swiper-pagination',
                autoplay: 5000
            },
            swiperList:[
                {
                    id: '0',
                    imgUrl: 'https://img1.qunarzz.com/vc/f3/ea/ae/095dd61c09f2797ba9147bd03f.jpg'
                },
                {
                    id: '1',
                    imgUrl: 'https://img1.qunarzz.com/vc/4e/c2/9a/61222b895136533c133ee9e8bc.jpg'
                },
                {
                    id: '2',
                    imgUrl: 'https://img1.qunarzz.com/vc/ce/4b/45/7f78e2003fb5fb65c57eb1a800.jpg'
                },
            ]
        }
    },
}
</script>

<style lang="stylus" scoped>
    .wrapper >>> .swiper-pagination-bullet-active
        background: #fff
    .wrapper
        overflow: hidden
        width: 100%
        height: 0
        padding-bottom: 32.5%
        img
            width: 100%

</style>
