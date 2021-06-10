<template>
  <section class="disks container">
      <div class="content" v-if="!loading" >
        <div class="col-12">
          <SelectGenre @performSelectGenre="selectGener" :gens="uniqueGenr"/>
        </div>
        <div class="col-12">
          <SelectArtist @performSelectArtist="selectArtist" :arts="uniqueArts"/>
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
import SelectArtist from './SelectArtist';
import axios from 'axios';
export default {
    name:"DisksList",
    components:{
        Disk,
        Loader,
        SelectGenre,
        SelectArtist
    },
    data: function() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            disks: [],
            uniqueGenr:[],
            uniqueArts:[],
            loading: true,
            selectFieldGenr:'',
            selectFieldArtist:''
        }
    },
    computed: {
        filteredDisks: function() {
            const newArray = this.disks.filter(
                (element) => {
                    return ((element.genre == this.selectFieldGenr || this.selectFieldGenr == "All" || this.selectFieldGenr == "" )  && (element.author == this.selectFieldArtist ||  this.selectFieldArtist == "" || this.selectFieldArtist == "All"));
                } 
            );
            return newArray;      
        }
    },
    methods: {
        selectGener: function(text){
            this.selectFieldGenr = text;
        },
        selectArtist: function(text){
            this.selectFieldArtist = text;
        }
    },
    created: function() {
        axios
            .get(this.apiUrl)
            .then(
               (response) => {
                   this.disks = response.data.response;
                   const genres =[];
                   const artists =[];
                   this.disks.forEach(element => {
                       genres.push(element.genre);
                       artists.push(element.author);
                   });
                   this.uniqueGenr = [...new Set(genres)];
                   this.uniqueArts = [...new Set(artists)];
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