<script>
// 1) Importazione del componente 
import AppTitle from './components/AppTitle.vue'

  export default {
  data() {
    return { 
        message: 'La mia prima app con Vite!'
    }
  },
  // 2) Dichiarizone del componente
  components: {
    AppTitle
  },
}
</script>

<template>
    <!-- Utilizzo del componente  -->
     <AppTitle />
  <div class="tittle">
    <h2>
      {{ message }}
    </h2>
  </div>

</template>

<style scoped>
.tittle {
  text-align: center;
}

.tittle > h2 {
  color: lightcoral;
}
</style>
