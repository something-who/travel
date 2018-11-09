<template lang="html">
    <div class="">
    
        <city-header></city-header>
    
        <city-search :cities="cities"></city-search>
    
        <city-List
            :cities="cities"
            :hot="hotCities"
            :letter="letter"
        >
        </city-List>
        <city-alphabet
            :cities="cities"
            @change="handleChange"
        ></city-alphabet>
    
    </div>
</template>

<script>
    
    import axios from "axios"
    import CityHeader from './components/Header'
    
    import CitySearch from './components/Search'
    
    import CityList from './components/List'
    
    import CityAlphabet from './components/Alphabet'
    
    export default {
        name: "City",
        data (){
            return{
                cities : {},
                hotCities : [],
                letter : ''
            }
        },
        components: {
            CityHeader,
            CitySearch,
            CityList,
            CityAlphabet
        },
        methods:{
            getCitiesInfo(){
                axios.get("/api/city.json")
                    .then(this.handleCityData)
            },
            handleCityData(res){
                res = res.data
                if(res.ret && res.data){
                    const data = res.data
                    // console.log(data)
                    this.cities = data.cities
                    this.hotCities = data.hotCities
                }
            },
            handleChange(e){
                // console.log(e)
                this.letter = e
            }
        },
        mounted () {
          this.getCitiesInfo()  
        }
    }
</script>

<style lang="stylus" scoped>
</style>
