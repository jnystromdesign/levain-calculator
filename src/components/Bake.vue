<template>
  <div class="popup">
    <div class="popup__overlay"></div>
    <div class="popup__body">
      <div class="popup__content">
        <button class="popup__close" @click="closePopup">X</button>
        <h2 class="popup__title">Time to bake! 🍞</h2>
        <ul>
          <li>Flour: {{ flour }}g</li>
          <li>Water: {{ water }}g</li>
          <li>Salt: {{ salt }}g</li>
        </ul>
        <button class="button" @click="closePopup">Ok. Close</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Bake",
  props: {
    availableLevain: Number,
    closePopup: Function
  },
  computed: {
    flour: function() {
      return this.availableLevain;
    },
    water: function() {
      return this.getProportion(550);
    },
    salt: function() {
      return this.getProportion(30);
    }
  },
  methods: {
    getProportion(amount) {
      return Math.floor((this.availableLevain / 800) * amount);
    }
  }
};
</script>

<style scoped lang="sass">

.popup

    &__overlay
        background-color: rgba(#333, .8 )
        position: fixed
        top: 0
        left: 0
        right: 0
        bottom: 0
        z-index: 3

    &__body
        max-width: 600px
        min-width: 480px
        background: #fff
        z-index: 4
        position: absolute
        left: 50%
        top: 50%
        border: 3px solid #ddd
        box-shadow: #00000040 -2px 2px 5px
        transform: translateX(-50%) translatey(-50%)

    &__content
        position: relative
        padding: 40px 20px

    &__close
      position: absolute
      top: -13px
      right: -13px
      background-color: #333
      color: #fff
      width: 40px
      height: 40px
      border-radius: 40px
      font-size: 1.4rem
      cursor: pointer

    &__title
      font-size: 1.4rem
      font-weight: bold
      margin: 0 0 1em

    button.button
      transition: all 200ms
      background-color: #fff
      -webkit-appearance: none
      display: block
      font-size: 1rem
      cursor: pointer
      border-radius: 5px
      padding: 1em 2em;
      margin-top: 1em
      border: 3px #ddd solid
      box-shadow: none
      margin: 40px auto 0
      text-transform: uppercase

      &:hover
          border-color: #bbb


    li
      font-size: 1.2rem
      margin-bottom: .5em
</style>
