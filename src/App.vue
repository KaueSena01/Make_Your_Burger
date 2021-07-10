<template>
  <Navbar :logo="logo_src" :alt="app_name"/>
  <router-view/>
  <Footer />
</template>

<script>
  import Navbar from './components/Navbar.vue'
  import Footer from './components/Footer.vue'

  export default{
    components: {
      Navbar, Footer
    },
    data() {
      return {
        logo_src: "/img/logo.png",
        app_name: "Make Your Burguer"
      }
    }
  }
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    margin: 0;
    font-family: Helvetica;
  }
  .main-container {
    margin: 50px;
    min-height: 280px;
  }

  h1{
    text-align: center;
    font-size: 42px; 
    margin-bottom: 30px;
    color:  #222;
  }
</style>
