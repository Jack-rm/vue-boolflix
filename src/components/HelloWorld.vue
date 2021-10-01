<template>
  <div class="hello">
  
    <h1>{{ msg }}</h1>
  
    <Header />
    <input type="text" placeholder="Movies" v-model='search' @keyup="executeSearch(search)">
    
    <ul>
      <li v-for="(card, index) in cardsList" :key="index">
        <Card :cardItem="card" />
      </li>
    </ul>
  
  </div>
</template>

<script>
import axios from 'axios';
import Header from '../components/Header.vue'
import Card from '../components/Card.vue'

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  components: {
      Header,
      Card,
  },
  data: function(){
    return{
      cardsList: [],
      search: '',
    }
  },
  methods:{
    executeSearch(search){
      console.log(search);
    }
  },

  created: function(){
    axios
    .get('https://api.themoviedb.org/3/search/movie?api_key=aa4ff77acc5aee627f260c508f92850e&query=ritorno+al+futuro')
    .then((response) =>{
      this.cardsList = [...response.data.results];
      console.log(this.cardsList)
    });
  }


}
</script>

<style scoped lang="scss">

ul {
  list-style-type: none;
  padding: 0;
}

</style>
