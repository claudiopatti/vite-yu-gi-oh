<script>
// 1) Importazione del componente 
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';


  export default {
  data() {
    return { 
    }
  },
  // 2) Dichiarizone del componente
  components: {
    AppHeader,
    AppMain
  },
}
</script>

<template>
    <!-- Utilizzo del componente  -->
     <AppHeader />

     <AppMain />


</template>

<style lang="scss" >
@use 'assets/scss/main.scss' as * ;

/* // Import all of Bootstrap's CSS */
@import "bootstrap/scss/bootstrap";
</style>
