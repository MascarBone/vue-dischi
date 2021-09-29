<template>
  <div class="my_disc">
      <div class="my_disc_img mb-3">
          <img :src="discItem.poster" :alt="discItem.title + ' - Album image'">
      </div>
      <div class="my_disc_text">
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
@import '../style/variables.scss';


.my_disc {
    background-color: $bgGreyLight;
    padding: 10px 15px;
    height: 100%;
}
.my_disc_img{
    height: 180px;
    display: flex;
    align-items: center;
    overflow: hidden;


    img {
        width: 100%;
    }
}

.my_disc_text {

    h2 {
        color: $colorWhite;
        font-size: 1.5rem;
    }
    p {
        color: $colorGrey;
        margin: 5px 0;
        font-size: 1.2rem;
    }
}

// @media screen and (min-width: 992px){
//     .disc_img{height: 250px;}
// }
// @media screen and (min-width: 768px){
//     .disc_img{height: 180px;}
// }
</style>