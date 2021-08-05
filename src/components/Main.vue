<template>

<div class="container">
  <div class="row">
    <div class="col-4 mt-3" v-for="(datadiri, index) in datadiris" :key="index">
      <div class="card border-warning mb-3" style="max-width: 35rem;">
        <div class="card-header bg-transparent border-warning display-5">Profil</div>
          <div class="card-body text-warning">
            <h4 class="card-title">{{datadiri.nama}}</h4>
            <p class="card-text">{{datadiri.alamat}}</p>
            <h5 class="card-title">{{datadiri.pendidikan}}</h5>
            <h5 class="card-title">{{datadiri.lahir}}</h5>
            <h5 class="card-title">{{datadiri.telp}}</h5>
            <h5 class="card-title">{{datadiri.kerja}}</h5>
            </div>
          <div class="card-footer bg-transparent border-warning">{{datadiri.kontak}}
          </div>
      </div>
    </div>
  </div>
</div>      
  <div class="card-footer text-muted">
    <router-link class="btn btn-light" :to="{name:'Editprofils', params:{id:datadiris.id}}"
              >Edit</router-link>
  </div>
</template>

<script>
export default {
    props: ["datadiris"],
}
</script>

<style>

</style>