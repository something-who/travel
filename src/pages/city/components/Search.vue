<template lang="html">
    <div>
        <div class="search">
            <input
                v-model="kword"
                class="search-input"
                type="text"
                name=""
                placeholder="输入城市名或者拼音"
            />
        </div>
        <div
            class="search-content"
            ref="search"
            v-show="kword"
        >
            <ul>
                <li
                    class="search-item border-bottom"
                    v-for="item of list"
                    :key="item.id"
                    @click="handCityClick(item.name)"
                >
                    {{item.name}}
                </li> 
                <li
                    class="search-item border-bottom"
                    v-if="hasNoData"
                >
                    无匹配数据
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import {mapMutations} from "vuex"
import Bscroll from "better-scroll"
export default {
    name: "CitySearch",
    props: {
        cities: Object
    },
    data () {
        return {
            kword: '',
            timer: null,
            list: [],
            // hasNoData: false
            // cities: {}
        }
    },
    methods: {
        handCityClick(city){
            this.changeCity(city)
            this.$router.push('/')
        },
        ...mapMutations(['changeCity'])
    },
    watch: {
        kword(){
            let result = []
            if(this.timer){
                clearTimeout(this.timer)
            }
            if(!this.kword){
                this.list = []
                return
            }
            // 函数截留
            this.timer = setTimeout(()=>{
                for(let i in this.cities){
                    this.cities[i].forEach((value) => {
                        if(value.spell.indexOf(this.kword) > -1 || value.name.indexOf(this.kword) > -1){
                            result.push(value)
                        }
                    })
                }
            }, 19)
            this.list = result
        }
    },
    computed:{
        // 逻辑与样式分离
        hasNoData() {
            return !this.list.length
        }
    },
    mounted(){
        this.scroll = new Bscroll(this.$refs.search)
    }
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
