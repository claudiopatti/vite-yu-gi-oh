<script>
// 1) Importazione del componente 
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';



  export default {
  data() {
    return { 
      allCardYugioh: []
    }
  },
  // 2) Dichiarizone del componente
  components: {
    AppHeader,
    AppMain
  },
  
  created() {
    axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
        .then((res) => {
            console.log(res)
            
            
            this.allCardYugioh = res.data.data;
            console.log(this.allCardYugioh)
        }

        )
  }
}
</script>

<template>
    <!-- Utilizzo del componente  -->
     <AppHeader />

     <AppMain :cards = "allCardYugioh" />


</template>

<style lang="scss" >
@use 'assets/scss/main.scss' as * ;

/* // Import all of Bootstrap's CSS */
@import "bootstrap/scss/bootstrap";
</style>
