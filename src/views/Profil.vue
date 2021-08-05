<template>
  <div class="home">

  <Main :profils="profils"/>
    
    <table class="table table-success table-stripe">
      <thead>
        <tr>
          <th scope="col">Nama</th>
          <th scope="col">No Telp</th>
          <th scope="col">NIK</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(pegawais, index) in pegawais" :key="index">
          <td>{{ pegawais.nama }}</td>
          <td>{{ pegawais.telp }}</td>
          <td>{{ pegawais.nik }}</td>
          <td>
            <router-link class="btn btn-light" :to="{name:'Editpegawais', params:{id:pegawais.id}}"
              >Edit</router-link
            >
            <button @click.prevent="pegawaiDelete(pegawai.id)" class="btn btn-secondary">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";
// @ is an alias to /src
import Main from "@/components/Main.vue";
import { onMounted, ref } from "vue";

export default {
  name: "Home",
  components: {
    Main,
  },

  setup() {
    let profil = ref([])

    onMounted(() => {
      axios
        .get('http://127.0.0.1:8000/api/profils')
        .then(response => {
          profil.value = response.data.data
        })
        .catch(error => {
          console.log(error)
        })
    })

    return {
      profil
    }
  }
};
</script>