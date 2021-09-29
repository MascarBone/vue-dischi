<template>
  <div class="container">
    <div class="row">
      <div class="col-2" v-for="(element,index) in listAlbum" :key="index">
        <Disc :discItem="element"/>
      </div>
    </div>  
  </div>
  
</template>

<script>
import axios from 'axios';

import Disc from './Disc.vue';

export default {
  name: 'Collection',

  data: function () {
    return {
      listAlbum: [],
    }
  },

  components: {
    Disc
  },

  created: function() {
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then((reply) => {
      console.log(reply.data.response);
      this.listAlbum = [...reply.data.response];
      console.log(this.listAlbum);
    })
  }
}
</script>

<style>
/* @import "~bootstrap/scss/bootstrap-grid"; */

</style>