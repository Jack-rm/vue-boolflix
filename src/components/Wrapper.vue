<template>
  <div class="hello">
  
    <Header @upSearch="executeSearch" />
    
    <main>
      <div class="container">
        <div class="row d-flex flex-wrap justify-content-center">
          <div class="col-12">
            <h2>Movies:</h2>
          </div>
          <div class="col-2 media-box gx-0" v-for="card in moviesList" :key="card.id">       
              <Card :cardItem="card" />
          </div>

        </div>
      </div>
      <div class="container">
        <div class="row d-flex flex-wrap justify-content-center">
          <div class="col-12">
            <h2>Tv Series:</h2>
          </div>

          <div class="col-2 media-box gx-0" v-for="card in tvSeriesList" :key="card.id">       
              <Card :cardItem="card" />
          </div>

        </div>
      </div>
    </main>

  </div>
</template>

<script>
import axios from 'axios';
import Header from './Header.vue'
import Card from './Card.vue'

export default {
  name: 'Wrapper',
  props: {
    msg: String,
  },
  components: {
      Header,
      Card,
  },
  data: function(){
    return{
      apiMoviesUrl: 'https://api.themoviedb.org/3/search/movie',
      apiSeriesUrl: 'https://api.themoviedb.org/3/search/tv',
      apiKey: 'aa4ff77acc5aee627f260c508f92850e',
      moviesList: [],
      tvSeriesList: [],
      search: '',
    }
  },
  methods:{

    /*
    executeSearch(search){
      axios
      .get('https://api.themoviedb.org/3/search/movie?api_key=aa4ff77acc5aee627f260c508f92850e&append_to_response=tv&query=' + search.trim())
      .then((response) =>{
        this.cardsList = response.data.results;
        // console.log(this.cardsList);
      });
      // console.log(search);
    }
    */

    executeSearch(search){
      if(search.length > 1){
        axios.get( this.apiMoviesUrl, {
          params: {
            api_key: this.apiKey,
            query : search,
            language :'it-IT',
          }
        }).then(
          (response) => {
            this.moviesList = [...response.data.results];
          })
          .catch(
            (errore) => {
              console.warn("Errore nella richiesta della API: ", errore);
            });

        axios.get( this.apiSeriesUrl, {
          params: {
            api_key: this.apiKey,
            query : search,
            language :'it-IT',
          }
        }).then(
          (response) => {
            this.tvSeriesList = [...response.data.results];
          })
          .catch(
            (errore) => {
              console.warn("Errore nella richiesta della API: ", errore);
            });
      }
    }
  },

}
</script>

<style scoped lang="scss">
@import '../style/general.scss';
@import '../style/variables.scss';

.media-box{
  margin-top: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
}

main {
  min-height: 100vh;
  background-color: $mainGrey;

  & h2{
    color: whitesmoke;
    padding-top: 20px;
  }
}


</style>
