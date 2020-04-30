<template>
  <div class="calculator">
    <InputWithControls
      :fieldValue="availableLevain"
      @increase="increaseField"
      @decrease="decreaseField"
      @change="updateField"
    />
    <div class="calculator__ingridients ingridients">
      <ValueDisplay label="Flour" v-bind:amount="flour" />
      <ValueDisplay label="Water" v-bind:amount="water" />
    </div>

    <Bake
      v-if="popupOpen"
      :availableLevain="availableLevain"
      :closePopup="closePopup"
    ></Bake>
    <Entries
      :currentLevainAmount="availableLevain"
      :setAvailableLevain="setAvailableLevain"
      :openPopup="openPopup"
    />
  </div>
</template>

<script>
import ValueDisplay from "./ValueDisplay";
import InputWithControls from "./InputWithControls";
import Entries from "./Entries";
import Bake from "./Bake";
export default {
  name: "Calculator",
  components: { ValueDisplay, InputWithControls, Entries, Bake },
  props: {
    initialAvailableLevain: {
      default: 270
    },
    popupOpen: {
      default: false
    }
  },
  data: function() {
    return {
      availableLevainData: this.initialAvailableLevain
    };
  },
  computed: {
    availableLevain: {
      get() {
        return this.availableLevainData;
      },
      set(value) {
        this.availableLevainData = value;
      }
    },
    flour: function() {
      return this.getProportion(220);
    },
    water: function() {
      return this.getProportion(160);
    }
  },
  methods: {
    getProportion: function(amount, baseAmount = 300) {
      return Math.floor((this.availableLevain / baseAmount) * amount);
    },
    updateField(value) {
      this.availableLevain = parseInt(value);
    },
    increaseField() {
      this.availableLevain = this.availableLevain + 10;
    },
    decreaseField() {
      this.availableLevain = this.availableLevain - 10;
    },
    setAvailableLevain(value) {
      this.availableLevain = value;
    },
    openPopup() {
      this.popupOpen = true;
    },
    closePopup() {
      this.popupOpen = false;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
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
  color: #42b983;
}
.ingridients {
  max-width: 100%;
  display: flex;
  width: 100%;
  justify-content: space-between;
}
</style>
