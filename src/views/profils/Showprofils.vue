<template>
 <div class="card text-center mt-4" v-for="p in datadiris" :key="p.id">
  <div class="card-header">
    Detail Pegawai
  </div>
  <div class="card-body">
    <h5 class="card-title">{{f.nama}}</h5>
    <p class="card-text">{{f.telp}}</p>
    <p class="card-text">{{f.nik}}</p>
    <p class="card-text">{{f.shift.name}}</p>

    <router-link class="btn btn-light" :to="{name:'Editpegawais', params:{id:f.id}}"
              >Edit</router-link
            >
            <button @click.prevent="pegawaiDelete(f.id)" class="btn btn-secondary">Delete</button>
  </div>
  
</div>
</template>

<script>
import { onMounted, ref } from "vue";
import { useRoute, useRouter } from "vue-router";
import axios from "axios";
export default {
  setup() {
    
    let datadiri = ref ([]);
    const router = useRouter();

    const route = useRoute();

    onMounted(()=>{
      axios.get(`http://127.0.0.1:8000/api/datadiris/`)
      .then(response => {
        console.log(response.data.data.nama)

        pegawai.value = response.data.data
      }).catch(error =>{
        console.log(error.response.data)
      })
    })

    return {
      datadiri,
      router,
      route
    };
  },
};
</script>

<style>

</style>