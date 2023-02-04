<template>
  <nav class="navbar navbar-light bg-light">
    <form class="form-inline">
      <button class="btn btn-outline-success" type="button">anterior</button>
      <button class="btn btn-sm btn-outline-secondary" type="button" @click="siguiente">siguiente</button>
    </form>
  </nav>
</template>
<script>
import axios from "axios";
import { response } from "express";
export default {
  name: 'barra_nav',
  data() {
    return {
      url: []
    }
  },
  methods: {
    siguiente(event) {
      event.preventDefault();
      axios.post('https://api.themoviedb.org/3/movie/now_playing?api_key=c4fea0df35b12e365355a05f0d1e905d&page=1&language=es-MX')
      .then((response) => {
        return this.url='https://api.themoviedb.org/3/movie/now_playing?api_key=c4fea0df35b12e365355a05f0d1e905d&page='+1+1+'&language=es-MX'
      })
    }
  }
}
</script>
<style scoped>

</style>