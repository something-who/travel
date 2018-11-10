<template lang="html">
    <div  class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom" >
                    当前城市
                </div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button" @click="handleCurrentCityClick">
                            {{this.city}}
                        </div>
                    </div>
                </div>
            <div class="area">
                <div class="title border-topbottom">
                    热门城市
                </div>
                <div class="button-list">
                    <div class="button-wrapper"
                        v-for="item of hot"
                        :key="item.id"
                        @click="handleCityClick(item.name)"
                    >
                        <div class="button">{{item.name}}</div>
                    </div>
                 </div>
                </div>
            </div>
            <div 
                class="area"
                v-for="(item, key) of cities"
                :key="key"
                :ref="key"
            >
                <div class="title border-topbottom" >
                    {{key}}
                </div>
                <div class="item-list">
                    <div
                        class="item border-bottom"
                        v-for="innerItem of item"
                        :key="innerItem.id"
                         @click="handleCityClick(innerItem.name)"
                    >
                        {{innerItem.name}}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import {mapState, mapMutations} from "vuex"
import Bscroll from "better-scroll"
export default {
    props: {
        hot: Array,
        cities: Object,
        letter: String
    },
    name: "CityList",
    methods: {
        handleCityClick(city){
            // console.log(city)
            this.changeCity(city)
            this.$router.push('/')
        },
        handleCurrentCityClick(){
            this.$router.push('/')
        },
        ...mapMutations(['changeCity'])
    },
    mounted () {
        this.scroll = new Bscroll(this.$refs.wrapper)
    },
    watch:{
        letter(){
            if(this.letter){
                
                this.scroll.scrollToElement(this.$refs[this.letter][0])
            }
        }
    },
    computed: {
        ...mapState(['city'])
    }
}
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
    .border-topbottom
        &:before
            border-color: #ccc
        &:after
            border-color: #ccc
    .border-bottom
        &:before
            border-color: #ccc
    .list
        position: absolute
        top: 1.58rem
        left: 0
        right: 0
        bottom: 0
        overflow: hidden
        .title
            line-height: .44rem
            background: #eee
            color: #666
            padding-left: .2rem
            font-size: .26rem
        .button-list
            overflow: hidden
            padding: .1rem .6rem .1rem .1rem
            .button-wrapper
                float: left
                width: 33.33%
                .button
                    margin: .1rem
                    padding: .1rem 0
                    text-align: center
                    border: .02rem solid #ccc
                    border-radius: .06rem
        .item-list
            // overflow:hidden
            .item
                line-height: .76rem
                color: #666
                padding-left: .2rem
</style>
