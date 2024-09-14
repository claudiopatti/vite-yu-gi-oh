<script>

  export default {
  data() {
    return {
    }
  },

  props: {
    cardYu: Object
  },
}
</script>

<template>
  

<div class="cardContainer h-100">
    <div>
        <img :src="cardYu.card_images[0].image_url" :alt="cardYu.name">
    </div>

    <div class="text-center pt-2">
        <p class="text-white text-uppercase fw-bold">
            {{ cardYu.name }}
        </p>
        <span>
            {{ cardYu.archetype }}
        </span>
        
    </div>

</div>
                
</template>

<style lang="scss" scoped>
.backgroundMain {
  background-color: #d48f38;
}

.cardContainer {
    background-color: #d48f38;
}
</style>
