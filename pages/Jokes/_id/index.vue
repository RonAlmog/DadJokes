<template>
  <div>
      <nuxt-link to="/jokes">Back to Jokes</nuxt-link>
       <h3>Single Joke</h3>      
    <h2>{{joke}}</h2>
    <hr>
    <small>Joke ID: {{$route.params.id}}</small>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      joke: []
    }
  },
  async created() {
    try {
      const config = {
        headers: { Accept: 'application/json' }
      }
      const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);
      this.joke = res.data.joke;

    } catch (error) {}
  }
}
</script>

<style>
</style>