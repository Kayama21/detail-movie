<template>
  <div class="profilecard">
    <header>
      <h1 class="font"> Daftar Film : </h1>
    </header>
    <br>
    <div class="row">
    <div class="col-md-3" v-for="(movie, index) in movies" :key="movie.id">
      <router-link :to="{ name: 'Movie', params: { id: index } }">
        <img class="poster" :src="movie.image" width="240p" height="360p"/>
          <br>
        <h2>{{ movie.title }}</h2>
      </router-link>
    </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      movies: []
    }
  },
  created () {
    this.getAllUser()
  },
  methods: {
    getAllUser () {
      axios.get('https://raw.githubusercontent.com/Kayama21/detail-movie/master/movie.json')
        .then((response) => {
          this.movies = response.data
          console.log(response.data)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>

<style scoped>
.profilecard {
  width: 80%;
  border-radius: 5px;
  background-color:whitesmoke;
  margin: auto;
  position: absolute;
  left: 0; right: 0;
}
.poster {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  border-radius: 5px;
}
.poster:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}
.font {
  font-family: fantasy;
}
</style>
