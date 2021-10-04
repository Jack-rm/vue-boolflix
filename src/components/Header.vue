<template>
    
    <section>
        <div class="container-fluid">
            <div class="row">
                <div class="col-12 d-flex justify-content-between align-items-center">
                    <div class="header-logo">
                        <img src="https://fontmeme.com/permalink/211001/4937b74c6317b36c509baa13669b4b20.png" alt="netflix-font" border="0">
                    </div>
                    <div class="header-utility mb-3">
                        <input type="text" class="form-control" placeholder=" Movies | Tv Series" v-model.trim="search" @keyup="$emit('upSearch', search)">    
                    </div>
                </div>
            </div>
      </div>
    </section>
    
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

<style lang="scss" scoped>
@import '../style/general.scss';
@import '../style/variables.scss';

section {
    background-color: $darkerGrey;
}
.header-logo{
    &img{
        height: 40px;
    }
}

.form-control{
    width: 250px;
}

</style>