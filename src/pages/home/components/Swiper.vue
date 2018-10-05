<template lang="html">
    <swiper
    :options="swiperOption" ref="mySwiper"
    class="wrapper"
    >
       <!-- slides -->
       <swiper-slide
       v-for="item of list"
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
    props: {
        list: Array
    },
    data(){
        return{
            swiperOption:{
                loop: true,
                pagination: '.swiper-pagination',
                autoplay: 5000
            }
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
