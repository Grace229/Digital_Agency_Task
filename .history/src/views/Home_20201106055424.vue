<template>
  <div class="home" >
    <v-container>
      <v-row>
        <v-col>
          
        </v-col>
      </v-row>
    </v-container>
   <Movies 
   v-for="movie in wholeResponse"
   :key="movie.id" :movie="movie"
   :loading="loading"  />
   
  <div class="text-center">
    <v-pagination
    v-if="wholeResponse.length > 0"
      v-model="page"
      :length="500"
      :total-visible="7"
      @input="next"
     

    ></v-pagination>
  </div>


  
  
  
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
import Movies from '@/components/Movies.vue'

export default {
  name: 'Home',
  components: {
  Movies,

  },
  data () {
    return {
      wholeResponse: [],
      totalPages: 0,
      page: 1,
      movies: [],
      loading: true
    }
  },

  watch: {
    async '$route.params' () {
      console.log(this.$route.query)
      try {
        let query = this.$route.query.q
        let data = await axios.get(`https://api.themoviedb.org/3/search/multi?api_key=55ae7e8ee068e60e2522e6c2e15994aa&language=en-US&page=${this.$route.query.q}&include_adult=false&query=${query}`)
         this.wholeResponse = data.data.results
      } catch (err) {
        
      }
    },
     async '$route.query.page' () {
      console.log(this.$route.query)
      try {
        let query = this.$route.query.q
        let data = await axios.get(`https://api.themoviedb.org/3/discover/movie?api_key=55ae7e8ee068e60e2522e6c2e15994aa&page=${this.$route.query.page}`)
         this.wholeResponse = data.data.results
          this.page = Number(data.page)
      } catch (err) {
        
      }
    }
  },
  
 async mounted () { 
 let response = await axios.get('https://api.themoviedb.org/3/discover/movie?api_key=55ae7e8ee068e60e2522e6c2e15994aa')
      this.wholeResponse = response.data.results
      this.page = Number(response.page)
      this.totalPages = Number(response.total_pages)
      this.loading = false 
  },
  methods: {
  next(e){
this.$router.push({ query: Object.assign({}, this.$route.query, { page: e }) });
  }
  }
  
}
</script>
<style scoped>
 .home{
      display: grid;
    grid-template-columns: repeat(4, 1fr);
    margin-bottom: 40px;
   }
</style>