<template>
    <div class="row row-cols-1 row-cols-md-5 mb-3 text-center">
        <div class="col" v-for="elemento in lista_peliculas" :key="elemento.id">
            <div class="card mb-4 rounded-3 shadow-sm">
                <div class="card-header py-3">
                    <h4 class="my-0 fw-normal" _msthash="1615172" _msttexthash="77701">{{ elemento.title }}
                    </h4>
                </div>
                <div class="card-body">
                    <h1 class="card-title pricing-card-title" _msthash="1615068" _msttexthash="60320">
                        {{ elemento.vote_average }}<small class="text-muted fw-light" _istranslated="1">/10</small></h1>
                    <div class="card-body">
                        <p>{{ elemento.overview }}</p>
                        <h5>{{ elemento.release_date }}</h5>

                    </div>
                   
                </div>
            </div>
        </div>

    </div>

</template>


<script>
import axios from "axios";
export default {
    name: 'catalogo',
    data() {
        return {
            lista_peliculas: []
        }
    },
    mounted() {
        this.ver_pelicula();
    },
    methods: {
       
        ver_pelicula() {
            axios.get('https://api.themoviedb.org/3/movie/now_playing?api_key=c4fea0df35b12e365355a05f0d1e905d&page=1&language=es-MX').then((response) => {
                this.lista_peliculas = response['data']['results'];
                

            })
                .catch((error) => {
                    console.log(error)
                })




        }
    },


}
</script>


<style scoped>
p {
    text-justify: auto;
}
</style>