<template>
  <div class="home">
    <Header />
    <Draw />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import Draw from '@/components/Draw.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'home',
  components: {
    Header,
    Draw,
    Footer
  }
}
</script>
