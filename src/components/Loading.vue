<template>
  <div class="loading-box">
      <p>Loading Screen</p>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss">
@import '../style/variables.scss';


.loading-box {
    background-color: $bgGreySoft;
    height: calc(100vh - 70px);
    display: flex;
    justify-content: center;
    align-items: center;

    p {
        font-size: 5rem;
        font-weight: 800;
        animation: aniload 0.4s linear infinite alternate-reverse;
    }

    @keyframes aniload {
        from {transform: scale(0.9);}
        to {transform: scale(1.1);}
    }
}
</style>