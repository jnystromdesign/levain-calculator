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
  </div>
</template>

<script>
import ValueDisplay from "./ValueDisplay";
import InputWithControls from "./InputWithControls";
export default {
  name: "Calculator",
  components: { ValueDisplay, InputWithControls },
  props: {
    initialAvailableLevain: {
      default: 300
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
    getProportion: function(amount) {
      return Math.floor((this.availableLevain / 300) * amount);
    },
    updateField(value) {
      this.availableLevain = parseInt(value);
    },
    increaseField() {
      this.availableLevain = this.availableLevain + 10;
    },
    decreaseField() {
      this.availableLevain = this.availableLevain - 10;
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
