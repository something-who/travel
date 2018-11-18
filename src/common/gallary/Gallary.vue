<template>
    <div class="container" @click="handleGallaryClick">
        <div class="wrapper">
            <swiper :options="swiperOption">
                <swiper-slide v-for="(item, index) of imgs" :key="index">
                    <img class="gallary-img" :src="item" alt="">
                </swiper-slide>
                 <div class="swiper-pagination"  slot="pagination"></div>
            </swiper>
        </div>
    </div>
</template>

<script>
export default {
    name: "CommonGallary",
    props: {
        imgs: {
            type: Array,
            default:function(){return []}
        }
    },
    data () {
        return {
            swiperOption: {
                pagination: ".swiper-pagination",
                observer: true,
                observeParents: true,
                paginationType: "fraction"
            }
        }
    },
    methods: {
        handleGallaryClick () {
            // emit chose events
            this.$emit("close")
        }
    },  
}
</script>

<style lang="stylus" scoped>
    .container >>> .swiper-container
        overflow inherit
    .container
        display flex
        flex-direction column
        // 垂直居中
        justify-content center
        z-index 99
        position: fixed
        // overflow: hidden
        left 0
        right 0
        top 0
        bottom 0
        background-color #000
        .wrapper
            height 0
            padding-bottom 100%
            .gallary-img
                width 100%
            .swiper-pagination
                color: #fff
                bottom: -1rem


</style>
