<template lang="html">
    <div class="">
    
        <city-header></city-header>
    
        <city-search></city-search>
    
        <city-List></city-List>
    
    </div>
</template>

<script>
    import CityHeader from './components/Header'
    
    import CitySearch from './components/Search'
    
    import CityList from './components/List'
    
    
    
    export default {
    
        name: "City",
    
        components: {
    
            CityHeader,
    
            CitySearch,
    
            CityList
    
        }
    
    }
</script>

<style lang="stylus" scoped>
</style>
