<template>
  <div class="disc">
      <div class="disc_img">
          <img :src="discItem.poster" :alt="discItem.title + ' - Album image'">
      </div>
      <div class="disc_text">
          <h2>{{discItem.title}}</h2>
          <p>{{discItem.author}}</p>
          <p>{{discItem.year}}</p>
          <p>{{discItem.genre}}</p>
      </div>
  </div>
</template>

<script>


export default {
    name: 'Disc',
    
    // props: {
    //     poster: String,
    //     title: String,
    //     author: String,
    //     genre: String,
    //     year: Number,
    // },

    props: {
        discItem: Object,
    },

    data: function() {
        return {
            vuoto: '',
        }
    }

}
</script>

<style lang="scss">

.disc_img{
    // height: 250px;
    // display: flex;
    // align-items: center;


    img {
        width: 100%;
    }
}

</style>