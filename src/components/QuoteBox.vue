

<template>
  <div :style="{ backgroundColor: selectedColor, transition: '0.3s ease-in' }" id='quote-box'>
    <p id="text">"{{quote.text}}"</p>
    <p id="author">— <em>{{quote.author}}</em></p>
    <a id='tweet-quote' title='Tweet this quote!' target='_top'><button :style="{ backgroundColor: selectedColor, transition: '0.3s ease-in' }"><i class='fa fa-twitter'></i></button></a>
    <button :style="{ backgroundColor: selectedColor, transition: '0.3s ease-in' }" id="new-quote" @click='getQuotes(); getColors()'>New Quote</button>
  </div>
</template>

<script>

export default {

  name: 'QuoteBox',
  props: ['quote'],
  data() {
    return { 
      colors: [
        '#974545',
        '#976E45',
        '#979745',
        '#6E9745',
        '#45976E',
        '#454897',
        '#6B4597',
        '#944597',
        '#974571',
        '#459781',
        '#458497'
      ],
      selectedColor: ''
    
    }
  },
  methods: {
    getQuotes() {
      this.$emit('getQuotes');
    },
    getColors() {
      let item = this.colors[Math.floor((Math.random() * this.colors.length))];
      setTimeout(() => {
        this.selectedColor = item;
      }, 300)
      
    }
  }
}
</script>

<style>

  #quote-box {
    width: 50%;
    border-radius: 10px;
    justify-content: center;
    text-align: center;
    margin: 0 auto;
    margin-top: 5em;
    padding: 50px;
  }

  p, #text {
    font-weight: 700;
    font-size: 20px;
    color: white;
  }

  p, #author {
    font-size: 13px;
    font-weight: 500;
    color: white;
  }

  button {
    font-family: 'Roboto Mono', monospace;
    border: none;
    border-radius: 5px;
    padding: 5px;
    cursor: pointer;
    height: 38px;
    color: white;
  }

  #tweet-quote {
    float: left;
  }

  button, #new-quote {
    float: right;
    font-weight: 600;
  }
</style>