<template>
  <div id="app">
    <h1>Leavin feeding calculator</h1>
    <img alt="Breado" src="./assets/bread.svg" />
    <Calculator />
  </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  name: "App",
  components: {
    Calculator
  }
};
</script>

<style lang="sass">
@import '~reset-css'

*
  box-sizing: border-box

#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  margin-top: 60px
  padding: 1em
  max-width: 800px
  margin: 0 auto
h1
  margin: 0 0 1em
  font-size: 2em
  font-weight: 900
  transform: rotate(-13deg) translateY(6em) translateX(-.5em)
  color: #fff
img
  max-width: 100%
</style>
