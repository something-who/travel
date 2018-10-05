<template lang="html">
    <div class="home">
        <home-header></home-header>
        <home-swiper></home-swiper>
        <home-swiper></home-swiper>

    </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
export default {
    name: 'Home',
    components: {
        HomeHeader,
        HomeSwiper
    }
}
</script>
<style media="screen" lang="stylus">

</style>
