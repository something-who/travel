<template lang="html">
    <div>
        <div class="search">
            <input
                class="search-input"
                type="text"
                name=""
                placeholder="输入城市名或者拼音"
            />
        </div>
        <!-- <div class="search-content">
            <ul>
                <li
                    class="search-item border-bottom"
                >
                    北京
                </li> 
            </ul>
        </div> -->
    </div>
</template>

<script>
export default {
    name: "CitySearch"
}
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
    .search
        height: .72rem
        padding: 0 .1rem
        background: $bgColor
        .search-input
              box-sizing: border-box
              width: 100%
              height: .62rem
              padding: 0 .1rem
              line-height: .62rem
              text-align: center
              border-radius: .06rem
              color: #666
    .search-content
        z-index: 1
        overflow: hidden
        position: absolute
        top: 1.58rem
        left: 0
        right: 0
        bottom: 0
        background: #eee
        .search-item
            line-hegiht: .62rem
            padding-left: .2rem
            background: #fff
            color: #666
</style>
