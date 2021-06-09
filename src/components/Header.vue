<template>
  <div>
      <img src="../assets/spotify.png" alt="Logo Spotify">
  </div>
</template>

<script>
export default {
    name:"Header"
}
</script>

<style lang="scss" scoped>
@import '../style/variables';
div{
    height:70px;
    background-color:$bg-color-shadow;
    img{
        height:100%;
        padding:10px 20px;
    }
}

</style>