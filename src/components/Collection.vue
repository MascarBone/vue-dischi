<template>
  <div class="my_bg_wrapper">
    <div class="container">
      <div v-if="loaded" class="row">
        <div class="col-12">
          <div class="row">

            <div class="col-3">
              <Selection :list="listGenre"/>
            </div>

            <div class="col-9">
              <div class="row justify-content-center">
                <div class="my_box-disc col-lg-2 col-3 mx-1 my-4" v-for="(element,index) in listAlbum" :key="index">
                  <Disc :discItem="element"/>
                </div>
              </div>              
            </div>
          </div>
        </div>
        
      </div>  
      <div v-else class="row">
        <div class="col-12">
          <Loading />
        </div>
      </div>
    </div>
  </div>   
</template>

<script>
import axios from 'axios';

import Disc from './Disc.vue';
import Loading from './Loading.vue';
import Selection from './Selection.vue';

export default {
  name: 'Collection',

  data: function () {
    return {
      listAlbum: [],

      loaded: false,

    }
  },

  computed: {

    /**
     * Proprietà computed che ritorna un array univoco dei generi musicali disponibili
     */
    listGenre: function() {
      return this.listAlbum.map(el => el.genre)
      // La funzione .map restituisce un array di pari lunghezza contenete solo i generi
      .filter((elemento, index, array) => {
        // La funzione .filter applicata a .map restituisce una sola volta il valore che trova nella lista
        // Se l'indice (index) non corrisponde all'indice (indexOf(elemento)) trovato, allora vuol dire che ne è presente più di uno
        // e non prosegue con l'inserimento di quest'ultimo
        console.log(elemento);
        console.log(index);
        console.log(array);
        console.log(array.indexOf(elemento));
        return array.indexOf(elemento) === index;

      });
    },
  },

  components: {
    Disc,
    Loading,
    Selection,
  },

  created: function() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((reply) => {
      
      this.listAlbum = [...reply.data.response];

      setTimeout(()=> {
        this.loaded = true;
      }, 1000)
    })
  }
}
</script>

<style lang="scss">
@import '../style/variables.scss';

  .my_bg_wrapper {
    background-color: $bgGreyDark;
  }
  .my_box-disc {
    text-align: center;
  }

</style>