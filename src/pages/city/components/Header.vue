<template lang="html">
    <div class="header">
    
        城市选择
    
        <router-link to="/">
    
            <div class="iconfont back-icon">
    
                &#xe624;
    
            </div>
        </router-link>
    
    </div>
</template>

<script>
    export default {
    
        name: "CityHead"
    
    }
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
    .header
        position: relative
        oveflow: hidden
        line-height: $headerHeight
        text-align: center
        background: $bgColor
        color: #fff
        font-size: .32rem
        .back-icon
            position: absolute
            top: 0
            left: 0
            width: .64rem
            text-align: center
            font-size: .4rem
            color: #fff
</style>
