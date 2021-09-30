<template>
  <div class="my_bg_wrapper">
    <div class="container">
      <div v-if="loaded" class="row">
        <div class="col-12">
          <div class="row">

            <div class="col-3">
              <div>                
                <SelectionGenre :list="listGenre" @genre-selection="changeGenre"/>
              </div>
              <div>
                <SelectionAuthor :list="listAuthor" @author-selection="changeAuthor"/>
              </div>

            </div>

            <div class="col-9">
              <div class="row justify-content-center">
                <div class="my_box-disc col-lg-2 col-3 mx-1 my-4" v-for="(element,index) in filteredList" :key="index">
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
import SelectionGenre from './SelectionGenre.vue';
import SelectionAuthor from './SelectionAuthor.vue';


export default {
  name: 'Collection',

  data: function () {
    return {
      listAlbum: [],

      loaded: false,

      selectedGenre: 'ALL',
      selectedAuthor: 'ALL',
    }
  },

  computed: {

    /**
     * Proprietà computed che ritorna un array univoco dei generi musicali disponibili
     */
    listGenre: function() {
      const tempArray = this.listAlbum.map(el => el.genre)
      // La funzione .map restituisce un array di pari lunghezza contenete solo i generi
      .filter((elemento, index, array) => {
        // La funzione .filter applicata a .map restituisce una sola volta il valore che trova nella lista
        // Se l'indice (index) non corrisponde all'indice (indexOf(elemento)) trovato, allora vuol dire che ne è presente più di uno
        // e non prosegue con l'inserimento di quest'ultimo

        // console.log(elemento);
        // console.log(index);
        // console.log(array);
        // console.log(array.indexOf(elemento));
        return array.indexOf(elemento) === index;
      });
      tempArray.sort();
      tempArray.unshift('ALL');
      return tempArray;
    },

    listAuthor: function() {
      const tempArray = this.filteredList.map(el => el.author)
      // La funzione .map restituisce un array di pari lunghezza contenete solo i generi
      .filter((elemento, index, array) => {
        // La funzione .filter applicata a .map restituisce una sola volta il valore che trova nella lista
        // Se l'indice (index) non corrisponde all'indice (indexOf(elemento)) trovato, allora vuol dire che ne è presente più di uno
        // e non prosegue con l'inserimento di quest'ultimo

        // console.log(elemento);
        // console.log(index);
        // console.log(array);
        // console.log(array.indexOf(elemento));
        return array.indexOf(elemento) === index;
      });
      tempArray.sort();
      tempArray.unshift('ALL');
      return tempArray;
    },

    /**
     * Array Filtrato per genere
     */
    filteredList: function() {
      if (this.selectedGenre.toLowerCase() != 'all')
      {
        if (this.selectedAuthor.toLowerCase() == 'all')
        {
          return this.listAlbum.filter(element => element.genre == this.selectedGenre)
        }else {
          return this.listAlbum.filter(element => element.genre == this.selectedGenre)
                                .filter(element => element.author == this.selectedAuthor);
        }

      } else if (this.selectedAuthor.toLowerCase() != 'all') {
          return this.listAlbum.filter(element => element.author == this.selectedAuthor)

        }

      return this.listAlbum;


      // if (this.selectedGenre.toLowerCase() == 'all')
      // {
      //   return this.listAlbum
      // }
      // return this.listAlbum.filter(element => element.genre == this.selectedGenre)
    }
  },

  methods: {
    changeGenre(el) {
      this.selectedGenre = el;
      this.selectedAuthor = 'ALL';
    },

    changeAuthor(el) {
      this.selectedAuthor = el;
    }
  },

  components: {
    Disc,
    Loading,
    SelectionGenre,
    SelectionAuthor,
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