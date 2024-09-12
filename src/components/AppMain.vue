<script>
import axios from 'axios';

  export default {
  data() {
    return {
        allCardYugioh: []
    }
  },
  created() {
    axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
        .then((res) => {
            
            this.allCardYugioh = res.data.data;
            console.log(this.allCardYugioh)
        }

        )
  }
}
</script>

<template>
  <div class="backgroundMain ">
        <header class="container">
        <div class="dropdown py-4 px-2">
            <a class="btn bg-white dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                <span class="pe-5">Alien</span>
            </a>

            <ul class="dropdown-menu">
                <li><a class="dropdown-item" href="#">Action</a></li>
            </ul>
            </div>

        </header>

        

        <main class="container bg-white p-5">
            
            <div class="row bg-black text-white ps-3 p-3 m-0">
                <span class="ps-0">found {{ allCardYugioh.length }} cards</span>
            </div>

            <div class="row">
                <div v-for="(cardYu, index) in allCardYugioh" :key="index" class="col-3 pb-4">
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
                </div>
            </div>
            


        </main>
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
