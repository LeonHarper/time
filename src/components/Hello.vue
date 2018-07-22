<template>
    <div id="app">
        <h1>{{days}} days {{hours}} hours {{minutes}} minutes and {{ seconds }} seconds</h1>
        <p>happiness : {{happiness}}</p>
        <p>energy : {{energy}}</p>
        <p>ticks : {{ticks}}</p>
        <br>
        <button v-on:click="sleepNight">Sleep</button>
        <br>
        <button v-on:click="play">Play</button>
        <TextOutput></TextOutput>
    </div>
</template>

<script>
import TextOutput from './TextOutput'
export default {
  name: 'hello',
  data () {
    return {
      ticks: 0,
      seconds: 0,
      minutes: 0,
      hours: 0,
      days: 0,
      weeks: 0,
      happiness: 60,
      energy: 57600
    }
  },
  methods: {
    tickClock: function () {
      this.ticks++
      this.seconds = this.ticks % 60
      this.minutes = Math.floor(this.ticks / 60) % 60
      this.hours = Math.floor(Math.floor(this.ticks / 60) / 60) % 24
      this.days = Math.floor(Math.floor(Math.floor(this.ticks / 60) / 60) / 24)
      this.spendHappiness(1)
      this.spendEnergy(1)
    },
    spendEnergy: function (quantity) {
      this.energy = this.energy - quantity
    },
    spendHappiness: function (quantity) {
      this.happiness = this.happiness - quantity
    },
    sleepNight: function () {
      this.ticks = this.ticks + 28800
      this.energy = this.energy = 57600
    },
    play: function () {
      this.ticks = this.ticks + 7200
      this.energy = this.energy - 7200
      this.happiness = this.happiness + 10
    }
  },
  components: {
    TextOutput
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
