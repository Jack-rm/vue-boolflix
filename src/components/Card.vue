<template>

  <div class="single-card" :style="{ backgroundImage: 'url(' + image + cardItem.poster_path + ')' }">
    <div class="card-info">
      <h3>{{ cardItem.title }}</h3>
      <span>{{ cardItem.original_title }} -- </span>
      <span>{{ cardItem.original_language.toUpperCase() }} </span><i :class="{'eng_flag':(cardItem.original_language == 'en'), 'ita_flag':(cardItem.original_language == 'it'), 'fas fa-globe':(cardItem.original_language != 'it' && cardItem.original_language != 'en')}"></i>
      <br>
      <span>({{ Math.round(cardItem.vote_average) }})</span>
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
      }
    }
}
</script>

<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.css';

.single-card{
  background-repeat: no-repeat;
  background-position: center;
  height: 500px;
}

.card-info{
  color: white;
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
}

</style>