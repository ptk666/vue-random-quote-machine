<template>
  <div id="app">
    <QuoteBox
    :quote='quotes'
    @getQuotes='getQuotes' />
    <Signature />
  </div>
</template>

<script>
import axios from 'axios'
import QuoteBox from './components/QuoteBox.vue'
import Signature from './components/Signature.vue'

export default {
  name: 'App',
  components: {
    QuoteBox,
    Signature
  },
  data() {
    return {
      quotes: {
        text: '',
        author: ''
      }
    }
  },
  mounted() {
    this.getQuotes();
  },
  methods: {
    async getQuotes() {
      try {
        const res = await axios.get('https://goquotes-api.herokuapp.com/api/v1/random?count=1');
        this.quotes = res.data.quotes[0];
      }
      catch(e) {
        console.log(e.message);
      }
    }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;1,100;1,200;1,300;1,400;1,500;1,600;1,700&display=swap');

  body {
    font-family: 'Roboto Mono', monospace;
    height: 100vh;
  }


</style>
