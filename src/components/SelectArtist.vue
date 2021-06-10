<template>
  <div>
    <select 
    v-model="selected"
    @click="$emit('performSelectArtist', selected)"
    >
      <option disabled value="">Seleziona un artista</option>
      <option>All</option>
      <option v-for="art,index in arts" 
      :value="art"
      :key="index">
            {{ art }}
      </option> 
   </select>
   
</div>
  
</template>

<script>
export default {
name:"SelectArtist",
    props: [ "arts" ],
    data: function(){
        return {
            selected:''
        }
    }
}
</script>


<style lang="scss" scoped>
    div{
        position: absolute;
        top:20px;
        right:200px;
       select{
        width:180px;
        padding:5px;
        background-color: white ;
    }
    }
    

</style>