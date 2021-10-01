<template>

  <div class="single-card">
      <p>{{ cardItem.title }}</p>
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