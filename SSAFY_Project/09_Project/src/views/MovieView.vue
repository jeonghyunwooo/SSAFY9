<template>
  <div>
    <MovieList/>
  </div>
</template>

<script>
import MovieList from '@/components/MovieList.vue'

export default {
  name:'MovieView',
  components:{
    MovieList,
  },
  created(){
    this.getMovies()
  },
  methods:{
    getMovies(){
      this.$store.dispatch('getMovies')
    }
  }
}
</script>

<style>

</style>