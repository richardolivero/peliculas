<template>
    <div class="row row-cols-1 row-cols-md-5 mb-3 text-center">
        <div class="col" v-for="elemento in lista_peliculas" :key="elemento.id">
            <div class="card mb-4 rounded-3 shadow-sm">
                <div class="card-header py-3" style="height: 70px;">
                    <h5 class="my-0 fw-normal" _msthash="1615172" _msttexthash="77701">{{ elemento.title }}
                    </h5>
                </div>
                <div class="card-body">

                    <div class="card-body">
                        <!-- <div class=" container text-wrap  text-truncate" style="height: 200px; width: 200px;"
                            id="texto">
                            {{ elemento.overview }}
                        </div> -->

                        <h5>{{ elemento.release_date }}</h5>
                        <div class="container"><a href=""></a><img v-bind:src="elemento.poster_path" alt="" width="100"
                                height="150"></div>

                    </div>
                    <div class="container " style="text-align:left;margin-top: auto;">
                        <div class="row">
                            <div class="col">
                                <h4 class="card-title pricing-card-title " _msthash="1615068" _msttexthash="60320"
                                    style="">
                                    {{ elemento.vote_average }}<small class="text-muted fw-light"
                                        _istranslated="1">/10</small>
                                </h4>
                            </div>
                            <div class="col" style="margin: -20% ; margin-left: 60%;">
                                <button type="button" class="btn btn-info">Info</button>
                            </div>
                        </div>


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
                let peliculas = response['data']['results'];
                peliculas.forEach(element => {
                    element.poster_path = 'https://image.tmdb.org/t/p/w500' + element.poster_path
                    this.lista_peliculas.push(element)

                });


                console.log(this.lista_peliculas)
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