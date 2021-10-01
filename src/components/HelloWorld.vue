<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" placeholder="Movies">
    <ul>
      <li v-for="(card, index) in cardsList" :key="index">
        <p>{{ card }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {},
  data: function(){
    return{
      cardsList: [],
    }
  },

  created: function(){
    axios
    .get('https://api.themoviedb.org/3/search/movie?api_key=aa4ff77acc5aee627f260c508f92850e&query=ritorno+al+futuro')
    .then((response) =>{
      this.cardsList = [response.data.results];
      console.log(this.cardsList)
    });
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
