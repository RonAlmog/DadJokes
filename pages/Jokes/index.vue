<template>
  <div>
      <h1>Joke</h1>
      <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke" >

      </Joke>
  </div>
</template>

<script>
import axios from 'axios';
import Joke from '@/components/Joke';
export default {
  data() {
    return {
      jokes: []
    }
  },
  components: {
      Joke
  },
  async created() {
    const config = {
      headers: { Accept: 'application/json' }
    }
    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config);
      this.jokes = res.data.results;

    } catch (error) {
      console.log(error)
    }
  },
  head() {
    return {
      title: 'Dad Jokes',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place to find dad jokes'
        }
      ]
    }
  }
}
</script>

<style>
</style>