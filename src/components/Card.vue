<template>

  <div class="single-card">
      <h3>{{ cardItem.title }}</h3>
      <span>{{ cardItem.original_title}} -- </span>
      <span>({{ cardItem.original_language }}) -- </span>
      <span>({{ cardItem.vote_average }})</span>
  </div>

</template>

<script>


export default {
    name: 'Card',
    props: ['cardItem'],
}
</script>

<style lang="scss">

</style>