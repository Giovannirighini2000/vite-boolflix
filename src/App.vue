<template>
  <AppMain @onSearch="feathMovies" />

  <cards v-for="card in store.card" :key="card.id" :card="card" />
</template>

<script >
import AppMain from './components/AppMain.vue'
import cards from './components/cards.vue'
import store from './store'
import axios from 'axios'

export default {
  components: {
    AppMain,
    cards,


  },
  data() {
    return {
      store
    }


  },
  methods: {
    feathMovies() {

      const search = this.store.search
      console.log('cards')
      axios
        .get(`https://api.themoviedb.org/3/search/movie?api_key=8926753f5fb24c80e369f9e81a562f21&query=${search}`,

        )
        .then((res) => {

          this.store.card = res.data.results
        })




    }

  },
  created() {
    this.feathMovies()
  }

}
</script>


<style ></style>
