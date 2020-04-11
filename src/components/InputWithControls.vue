<template>
  <div>
    <label for="levain_available">Levain available</label>
    <div class="levain-input-controls">
      <button class="btn decrease" @click="$emit('decrease')">-</button>

      <input
        v-bind:value="fieldValue"
        @input="$emit('change', $event.target.value)"
        name="levain_available"
        id="levain_available"
        class="levain-input"
        type="number"
        min="50"
        pattern="[0-9]*"
        inputmode="numeric"
      />

      <button class="btn increase" @click="$emit('increase')">+</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "InputWithControls",
  props: ["fieldValue"]
};
</script>

<style lang="scss">
.btn {
  -webkit-appearance: none;
  display: block;
  width: 5rem;
  flex: 0 0 auto;
  font-size: 3rem;
  cursor: pointer;
  border-radius: 10px 0 0 10px;

  .levain-input + & {
    border-radius: 0 10px 10px 0;
  }
  &:hover {
    background-color: #f8f8f8;
  }
  &:active {
    background-color: #eee;
  }
}
.levain-input {
  flex: 1 1 100%;
}
.levain-input-controls {
  display: flex;
  margin-bottom: 1em;
  margin-top: 1em;

  label {
    display: block;
    font-size: 1.3em;
    font-weight: 900;
    text-transform: uppercase;
    color: #999;
    margin-bottom: 0.25em;
  }
  input {
    width: 100%;
  }
}
#levain_available {
  font-size: 3em;
  background-color: #333;
  color: #fff;
  padding: 1rem;
  text-align: center;

  border: none;
}
</style>
