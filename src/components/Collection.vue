<template>
  <div class="my_bg_wrapper">
    <div class="container">
      <div class="row justify-content-center">
        <div class="my_box-disc col-lg-2 col-3 mx-1 my-4" v-for="(element,index) in listAlbum" :key="index">
          <Disc :discItem="element"/>
        </div>
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

<style lang="scss">
@import '../style/variables.scss';

  .my_bg_wrapper {
    background-color: $bgGreyDark;  
  }
  .my_box-disc {
    text-align: center;
  }
</style>