<template>
  <div id="app">
    <h1>Levain feeding calculator</h1>
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

@keyframes wooble
  from
    transform: rotate(5deg)
  to
    transform: rotate(-2deg)

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
  font-size: 5vw;
  font-weight: 900
  transform: rotate(-13deg) translateY(6em) translateX(-.5em)
  color: #fff
  text-shadow: #CAA459 2px 1px 0px
  position: relative
  z-index: 2
  @media screen and (min-width: 800px)
    font-size: 2em

img
  max-width: 100%
  animation: wooble 1400ms ease-out alternate infinite
  position: relative
  z-index: 1
</style>
