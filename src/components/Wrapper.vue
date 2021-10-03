<template>
  <div class="hello">
  
    <Header @upSearch="executeSearch" />
    
    <main>
      <div class="container">
        <div class="row d-flex justify-content-center">
          <div class="col-2 media-box gx-0" v-for="(card, index) in cardsList" :key="index">
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
      cardsList: '',
      search: '',
    }
  },
  methods:{
    executeSearch(search){
      axios
      .get('https://api.themoviedb.org/3/search/movie?api_key=aa4ff77acc5aee627f260c508f92850e&append_to_response=tv&query=' + search.trim())
      .then((response) =>{
        this.cardsList = response.data.results.slice();
        // console.log(this.cardsList);
      });
      // console.log(search);
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
}


</style>
