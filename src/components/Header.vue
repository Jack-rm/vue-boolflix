<template>
    <div>
        <img src="https://fontmeme.com/permalink/211001/4937b74c6317b36c509baa13669b4b20.png" alt="netflix-font" border="0">
        <br>
        <input type="text" placeholder="Movies" v-model="search" @keyup="$emit('upSearch', search)">    
    </div>

</template>

<script>


export default {
    name: 'Header',
    props: {
    },
    data() {
        return {
            search: '',
        }
    },
}


</script>

<style lang="scss">

</style>