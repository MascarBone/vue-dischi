<template>
  <div class="my_bg_wrapper">
    <div class="container">
      <div v-if="loaded" class="row justify-content-center">
        <div class="my_box-disc col-lg-2 col-3 mx-1 my-4" v-for="(element,index) in listAlbum" :key="index">
          <Disc :discItem="element"/>
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
import Loading from './Loading.vue'
export default {
  name: 'Collection',

  data: function () {
    return {
      listAlbum: [],

      loaded: false,
    }
  },

  components: {
    Disc,
    Loading
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