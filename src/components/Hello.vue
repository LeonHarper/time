<template>
    <div id="app">
        <h1>{{minutes}} minutes and {{ seconds }} seconds</h1>
        <p>ticks : {{ticks}}</p>
        <br>
        <button v-on:click="tickClock">Tick Clock</button>
    </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      ticks: 55,
      seconds: 55,
      minutes: 0
    }
  },
  methods: {
    tickClock: function () {
      this.ticks++
      if (this.seconds < 60) {
        this.seconds++
      } else {
        this.seconds = 1
        this.minutes++
      }
    }
  },
  mounted () {
    setInterval(this.tickClock, 1000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #35495E;
}
</style>
