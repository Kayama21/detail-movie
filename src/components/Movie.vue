<template>
    <div class="profilecard">
        <div class="container">
    <div class="row justify-content-md-center mt-5 pt-3">
      <div class="col-md-4">
        <img class="poster" :src="movie.image" width="360p" height="540p"/>
      </div>
      <div class="col-md-7 content">
        <div class="card">
          <div class="card-header">
            <h2>
              {{ movie.title }}
              <span class="badge badge-primary">New</span>
            </h2>
          </div>
          <div class="card-body">
            <blockquote class="blockquote mb-0">
              <img src='../assets/star.png' width="36" height="36"/> {{ movie.skor }}
              <p>Genre : {{ movie.genre }} </p>
              <p>Durasi : {{ movie.durasi }}</p>
              <p>Rating Umur : {{ movie.rating }}</p>
              <p>Sutradara : {{ movie.sutradara }}</p>
            </blockquote>
          </div>
        </div>
        <hr class="divider" />
        <div class="alert alert-light">
          <h5 class="alert-heading">SINOPSIS</h5>
          <hr />
          <h5 class="font-weight-light mb-0">{{ movie.sinopsis }}</h5>
          <hr />
        </div>
        <router-link to="/" class="btn btn-success"> Back </router-link>
      </div>
    </div>
  </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      movie: []
    }
  },
  created () {
    this.getUser()
  },
  methods: {
    getUser () {
      axios.get('https://raw.githubusercontent.com/Kayama21/detail-movie/master/movie.json')
        .then((response) => {
          this.movie = response.data[this.$route.params.id]
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
  margin-top: 30px;
  margin-bottom: 30px;
}
.poster:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}
.font {
  font-family: fantasy;
}
.content {
  margin-top: 20px;
}
</style>
