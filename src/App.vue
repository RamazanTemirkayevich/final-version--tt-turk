<template>
  <div class="app">
    <Header/>
    <Subheader/>
    <Promo/>
    <Description/>
    <Carousel/>
    <Review/>
    <Footer/>
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Subheader from './components/Subheader.vue'
import Promo from './components/Promo.vue'
import Description from './components/Description.vue'
import Carousel from './components/Carousel.vue'
import Review from './components/Review.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Subheader,
    Promo,
    Description,
    Carousel,
    Review,
    Footer
  }
}
</script>