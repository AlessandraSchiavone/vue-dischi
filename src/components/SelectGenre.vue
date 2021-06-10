<template>
<div>
    <select 
    v-model="selected"
    @click="$emit('performSelect', selected)"
    >
      <option disabled value="">Seleziona un genere</option>
      <option>All</option>
      <option v-for="gen,index in gens" 
      :value="gen"
      :key="index">
            {{ gen }}
      </option> 
   </select>
   
</div>
  
</template>

<script>
export default {
    name:"SelectGenre",
    props: [ "gens" ],
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
        right:10px;
       select{
        width:180px;
        padding:5px;
        background-color: white ;
    }
    }
    
</style>