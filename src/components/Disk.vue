<template>
  <div class="disk text-center">
    <img class="img-fluid" :src="item.poster" :alt="item.title">
    <h3>{{ item.title }}</h3>
    <div>
        {{ item.author }} <br>
        {{ item.year }}
    </div>
  </div>
</template>

<script>
export default {
    name: "Disk",
    props: [ "item" ]
}
</script>

<style lang="scss" scoped>
@import '../style/variables';
.disk{
    background-color:$bg-color-shadow;
    height:360px;
    margin-left:40px;
    padding:15px;
    margin-top:20px;
    img{
       padding:5px;
    }
    h3{
        color:white;
        text-transform: uppercase;
        padding:15px 5px;
        font-weight: 700;
        text-shadow: 1px 1px 1px;
        font-size: 23px;
    }
    div{
        color:$text-color;
        line-height: 1.2;
        font-size: 19px;
    }
}

</style>