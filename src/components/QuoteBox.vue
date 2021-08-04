<template>
  <div id='quote-box'>
    <p id="text">"{{quote.text}}"</p>
    <p id="author">— <em>{{quote.author}}</em></p>
  </div>
</template>

<script>

export default {
name: 'QuoteBox',
props: ['quote']
}
</script>

<style>
  #quote-box {
    background-color: red;
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
    color: white;
  }
</style>