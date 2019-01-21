<template>
    <div>
        <div class="header-abs">
            <router-link tag="div" to="/">
                <div class="iconfont header-abs-back">&#xe624;</div>
            </router-link>
        </div>
        <div 
            class="header-fixed"
            v-show="isShowAbs"
            :style="opacityStyle"
        >
            <router-link tag="div" to="/">
                <div class="iconfont header-fixed-icon">&#xe624;</div>
                景点详情 
            </router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: "DetailHeader",
    data () {
        return {
            isShowAbs: false,
            opacityStyle: {
                opacity: 0
            }
        }
    },
    methods : {
        handleScroll () {
            const top = document.documentElement.scrollTop || document.body.scrollTop || window.pageYOffset
            // console.log(top)
            if(top > 40 && top < 140){
                let opacity = top/140
                opacity = opacity > 1 ? 1 : opacity
                this.opacityStyle = {opacity}
                this.isShowAbs = true
            } else if (top > 140) {
                this.isShowAbs = true
                // console.log(this.isShowAbs)
                // this.opacityStyle = {opacity: 1}
            }else {
                this.isShowAbs = false
            }
        }
    },
    mounted () {
        // listen window's scroll
        window.addEventListener("scroll", this.handleScroll)
    },
    unmounted () {
        // 全局事件的解绑, 
        window.removeEventListener('scroll', this.handleScroll)
    }
}
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
    .header-abs
        position: absolute
        top: .2rem
        left .2rem
        width .8rem
        height .8rem
        line-height .8rem
        text-align center
        border-radius 4rem
        background-color: rgba(0, 0, 0, .8)
        .header-abs-back
            font-size .4rem
            color #fff
    .header-fixed
        z-index 2
        position: fixed
        top: 0
        left 0
        right 0 
        line-height: $headerHeight
        text-align: center
        background: $bgColor
        color: #fff
        font-size: .32rem
        .header-fixed-icon
            position: absolute
            top: 0
            left: 0
            width: .64rem
            text-align: center
            font-size: .4rem
            color: #fff
</style>
