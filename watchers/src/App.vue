
<template>
  <h2>Volume Tracker (0-20)</h2>
  <h3>Current Volume: {{ volume }}</h3>
  <button @click="volume += 1">Increase</button>
  <button @click="volume -= 1">Decrease</button>
  <br>
  <input type="text" v-model="movie">
  <input type="text" v-model="movieInfo.title">
  <input type="text" v-model="movieInfo.actor">
</template>

<script>
  export default {
    data() {
      return {
        volume: 0, 
        movie: 'spiderman',
        movieInfo: {
          title: '',
          actor: ''
        }
      }
    },
    computed: {},
    methods: {
      blur() {
        console.log(this.movie)
      }
    },
    watch: {
      volume(newValue, oldValue) {
        console.log("new: " + newValue +  " old: " + oldValue)
        if (newValue === 15 && newValue > oldValue) {
          alert("Listening to a high volume for a long time may damage your hearing");
        }
      },      
      // movie(newValue) { // wathing on template change
      //   console.log(newValue)
      // },      
      movie: { 
        handler(newValue) {
          console.log(newValue)
        },
        immediate: true // watching on data property load
      },
      movieInfo: {
        handler(newValue) {
          console.log(`Calling API with movie title = ${newValue.title} and actor = ${newValue.actor}`)
        },
        deep: true
      }
    }
  }
  
</script>



<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
