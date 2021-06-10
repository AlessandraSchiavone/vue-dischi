<template>
  <section class="disks container">
      <div class="content" v-if="!loading" >
        <div class="col-12">
          <SelectGenre @performSelect="selectGener" :gens="uniqueGenr"/>
        </div>
          <div 
            class="card-disk" 
            v-for="disk,index in filteredDisks"
            :key="index"    
            >
            <Disk
                :item="disk"
            /> 
          </div>  
      </div>
      <Loader v-else/> 
  </section>
</template>

<script>
import Disk from './Disk';
import Loader from './Loader';
import SelectGenre from './SelectGenre';
import axios from 'axios';
export default {
    name:"DisksList",
    components:{
        Disk,
        Loader,
        SelectGenre
    },
    data: function() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            disks: [],
            uniqueGenr:[],
            loading: true,
            selectField:''
        }
    },
    computed: {
        filteredDisks: function() {
            // console.log("Filtered disks");
            if(this.selectField == "All" || this.selectField == ""){
                return this.disks;
            }
            const newArray = this.disks.filter(
                (element) => {
                    return element.genre == this.selectField;
                } 
            );
            return newArray;      
        }
    },
    methods: {
        selectGener: function(text){
            this.selectField = text;
        }
    },
    created: function() {
        axios
            .get(this.apiUrl)
            .then(
               (response) => {
                   this.disks = response.data.response;
                   const genres =[];
                   this.disks.forEach(element => {
                       genres.push(element.genre);
                   });
                   this.uniqueGenr = [...new Set(genres)];
                   this.loading = false;   
               }
            )
            .catch();    
    } 
}
</script>

<style lang="scss" scoped>
@import '../style/variables';

.disks{
    padding:50px;
    .content{
        display:flex;
        flex-wrap: wrap;
        .card-disk{
            width:calc(100% / 5);
            margin-bottom:5px;
             &:hover{
                cursor: pointer;
                transform: scale(1.1);
            }
        }
    }
   
}


</style>