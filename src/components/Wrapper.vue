<template>
  <div class="hello">
  
    <h1>{{ msg }}</h1>
  
    <Header @upSearch="executeSearch" />
    
    <ul>
      <li v-for="(card, index) in cardsList" :key="index">
        <Card :cardItem="card" />
      </li>
    </ul>
  
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
      cardsList: '',
      search: '',
    }
  },
  methods:{
    executeSearch(search){
      axios
      .get('https://api.themoviedb.org/3/search/movie?api_key=aa4ff77acc5aee627f260c508f92850e&query=' + search.trim())
      .then((response) =>{
        this.cardsList = response.data.results;
        console.log(this.cardsList)
      });
      console.log(search);
    }
  },


}
</script>

<style scoped lang="scss">

ul {
  list-style-type: none;
  padding: 0;
}

</style>
