<template lang="html">
    <div class="">
        <div class="title">
            <img src="http://img1.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png" alt="热门推荐">
            <span>热门推荐</span>
        </div>
        <ul >
            <router-link :to="'/detail/'+item.id" tag="li" class="item border-bottom" v-for="item of list" :key="item.id">
                <img class="item-img" :src="item.imgUrl" :alt="item.title">
                <div class="item-info">
                    <p class="item-title">
                        {{item.title}}
                    </p>
                    <p class="item-desc">
                        {{item.desc}}
                    </p>
                    <button class="item-button">查看详情</button>
                </div>

            </router-link>
        </ul>
    </div>
</template>
<script>
export default {
    name: 'HomeRecommend',
    props: {
        list: Array
    },
    data(){
        return {
        }
    }
}
</script>

<style lang="stylus" scoped>
    @import '~style/mixins.styl'
    .title
        margin-top: 0.2rem
        line-height:.9rem
        text-indent:.2rem
        color: #212121;
        font-size: .35rem
        ellipsis()
        img
            width: .4rem
    .item
        overflow: hidden
        display: flex
        height: 1.9rem
        .item-img
            width: 1.7rem
            height: 1.7rem
            padding: .1rem
        .item-info
            flex: 1
            padding: .1rem
            min-width: 0
            .item-title
                line-height: .54rem
                font-size: .32rem
                ellipsis()
            .item-desc
                line-height: .4rem
                color: #ccc
                ellipsis()
            .item-button
                line-height: .44rem
                margin-top: .16rem
                background: #ff9300
                padding: 0 .2rem
                border-radius: .06rem
                color: #fff
                // float: right

</style>
