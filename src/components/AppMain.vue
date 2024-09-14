<script>
import { store } from '../store';
import singleCard from './singleCard.vue';
import axios from 'axios';


  export default {
  data() {
    return {
        store,
        allTypeCards: [],
        searchTypeCard: '',
       
    }
},

methods: {
    searcheForArchetype() {
        console.log('cliccato')
        // if (this.searchTypeCard != '') {
            
        // }
        axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0' , {
            params: {
                archetype: this.searchTypeCard,
            }
        })
        .then((res) => {
            console.log(res)
            
            
            this.store.allCardYugioh = res.data.data;
            console.log(this.store.allCardYugioh)
        })
        .catch((err) => {

        })
}
},

components: {
    singleCard
    
},
props: {
  cards: Array
},
  created() {
    axios
        .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then((risultato) => {
            
            
            this.allTypeCards = risultato.data;
            console.log(risultato.data)
            console.log(this.allTypeCards[0].archetype_name)
            
        }

        )
  },
}
</script>

<template>
  <div class="backgroundMain ">
        <header class="container p-3">
                        
            {{ searchTypeCard }}
            <select v-model="searchTypeCard" @click="searcheForArchetype()" id="cars" class="py-2 pe-5">
                <option   v-for="(type, index) in allTypeCards" :key="index" 
                :value="type.archetype_name">
                {{ type.archetype_name }}
                </option>
            </select>
            
        <!-- <div class="dropdown py-4 px-2">
            <a class="btn bg-white dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                <span class="pe-5">Alien</span>
            </a>

            <ul class="dropdown-menu">
                <li><a class="dropdown-item" href="#">Action</a></li>
            </ul>
            </div> -->

        </header>

        

        <main class="container bg-white p-5">
            
            <div class="row bg-black text-white ps-3 p-3 m-0">
                <span class="ps-0">found {{ store.allCardYugioh.length }} cards</span>
            </div>

            <div class="row">
                <div v-for="(cardYu, index) in store.allCardYugioh" :key="index" class="col-3 pb-4">
                    <single-card :cardYu = "cardYu" />
                    <!-- <div class="cardContainer h-100">
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

                    </div> -->
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
