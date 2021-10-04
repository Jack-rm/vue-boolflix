<template>

  <div class="single-card" :style="{ backgroundImage: 'url(' + image + cardItem.poster_path + ')' }">
    
    <div class="card-info">
      <ul>
        <li>
          <h4>{{ cardItem.title ? cardItem.title : cardItem.name }}</h4>
          </li>
        <li>
          <span>{{ cardItem.original_title }}</span>
          </li>
        <li>
          <span>{{ cardItem.original_language.toUpperCase() }} </span>
          <i :class="{'eng_flag':(cardItem.original_language == 'en'),
                      'ita_flag':(cardItem.original_language == 'it'),
                      'fas fa-globe':(cardItem.original_language != 'it' && cardItem.original_language != 'en')}">
          </i>
        </li>
        <li><i class="fas fa-star" v-for="rating in ratingCap" :class="{'current_rating':((Math.round(cardItem.vote_average / 2) >= rating))}" :key="rating"></i><span></span>
        </li>
      </ul>
    </div>

  </div>

</template>

<script>


export default {
    name: 'Card',
    props: ['cardItem'],
    data() {
      return {
        image: 'https://image.tmdb.org/t/p/w342',
        ratingCap: [1, 2, 3, 4, 5],
        // current_value : null,
      }
    },
    methods: {
      /*
      set: function(value) {
        this.current_value = value;
        return this.value = value;
      }
      */
    },
}
</script>

<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.css';
@import '../style/variables.scss';
@import '../style/general.scss';

ul{
  list-style-type: none;
  padding: 10px;
}

.single-card{
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
  margin: 5px;
  width: 200px;
  height: 275px;
}

.card-info{
  color: white;
  background-color: black;
  height: 100%;
  width: 100%;
  opacity: 0;
    
    &:hover{
      opacity: 0.9;
    }
}

.eng_flag{
  display: inline-block;
  width: 50px;
  height: 15px;
  background-image: url('https://upload.wikimedia.org/wikipedia/commons/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg');
  background-size: contain;
  background-repeat: no-repeat;
}

.ita_flag{
  display: inline-block;
  width: 50px;
  height: 15px;
  background-image: url('https://upload.wikimedia.org/wikipedia/commons/0/03/Flag_of_Italy.svg');
  background-size: contain;
  background-repeat: no-repeat;
}

.fas{
  font-size: 1.3em;
  &.current_rating{
    color: $myGolden;
  }
}

</style>