<template>
  <section class="disks container">
      <div class="content" v-if="!loading" >
          <div 
            class="card-disk"
            v-for="disk,index in disks"
            :key="index"    
            >
              <disk
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
import axios from 'axios';
export default {
    name:"DisksList",
    components:{
        Disk,
        Loader
    },
    data: function() {
        return {
            apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
            disks: [],
            loading: true
        }
    },
     created: function() {
        axios
            .get(this.apiUrl)
            .then(
               (response) => {
                   this.disks = response.data.response;
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