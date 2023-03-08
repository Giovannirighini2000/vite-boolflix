<template>
  <AppHeader @onSearch="feathMovies" />

  <AppMain />
  <div class="background-base-black">
    <div class="container-2">
      <h4 class="mini-title">
        La tua Ricerca
        .....
      </h4>
      <div class="flex wrap gap">
        <cards v-for="content in store.allcontent" :key="content.id" :card="content" />
      </div>


    </div>
  </div>
</template>

<script >
import AppMain from './components/AppMain.vue'
import cards from './components/cards.vue'
import store from './store'
import axios from 'axios'
import AppHeader from './components/AppHeader.vue'

export default {
  components: {
    AppMain,
    cards,
    AppHeader,


  },
  data() {
    return {
      store
    }


  },
  methods: {
    feathMovies() {

      const search = this.store.search
      axios.all([
        axios
          .get(`https://api.themoviedb.org/3/search/movie?api_key=8926753f5fb24c80e369f9e81a562f21&query=${search}`),

        axios
          .get(`https://api.themoviedb.org/3/search/tv?api_key=8926753f5fb24c80e369f9e81a562f21&query=${search}`)

      ]


      )
        .then((res) => {
          const Searchmovies = res[0].data.results
          const Searchseries = res[1].data.results
          this.store.tvShows = Searchmovies
          this.store.card = Searchseries
          this.store.allcontent = [...Searchmovies, ...Searchseries]

        })








    }

  },
  created() {
    this.feathMovies()
  }

}
</script>


<style lang="scss">
@use'./style/general.scss'
</style>
