<template lang="html">
    <ul class="list">
        <li
            class="item"
            v-for="item of letters"
            :key="item"
            :ref="item"
            @click="handleClick"
            @touchstart="handleTouchStart"
            @touchmove="handleTouchMove"
            @touchend="handleTouchEnd"
            >{{item}}</li>
    </ul>
</template>
<script>
    export default {
        name: "CityAlphabet",
        props: {
            cities: Object
        },
        // computed property
        computed:{
            letters(){
                let letters = []
                for(let i in this.cities){
                    letters.push(i)
                }
                return letters
            }
        },
        data(){
            return{
                isTouch : false,
                startY: 0,
                timer: null
            }
        },
        updated(){
            this.startY = this.$refs['A'][0].offsetTop;
        },
        methods: {
            handleClick(e){
                // console.log(e.target.innerText)
                this.$emit("change", e.target.innerText)
            },
            handleTouchEnd(e){
                this.isTouch = false
            },
            handleTouchMove(e){
                if(this.isTouch){
                    if(this.timer){
                        clearTimeout(this.timer)
                    }
                    this.timer = setTimeout(()=>{
                        const currentY = e.touches[0].clientY - 79
                        const index = Math.floor((currentY - this.startY) / 20)
                        if(index >= 22){
                            return
                        }
                        this.$emit("change",this.letters[index])
                    }, 16)
                    // console.log(this.letters[index])
                }
            },
            handleTouchStart(e){
                this.isTouch = true
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~style/varibles.styl'
    .list
        display: flex
        flex-direction: column
        justify-content: center
        position: absolute
        top: 1.58rem
        right: 0
        bottom: 0
        width: .4rem
        .item
            line-height: .4rem
            text-align: center
            color: $bgColor
</style>
