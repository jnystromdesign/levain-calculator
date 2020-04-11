<template>
  <tr>
    <td>{{ entry.val }}</td>
    <td>{{ flour }}</td>
    <td>{{ water }}</td>
    <td>{{ total }}</td>
    <td>
      <button @click="removeEntry(entry.date)" class="remove">🗑</button>
      <button @click="useItem(total)" class="add">Use</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "Entry",
  props: {
    entry: Object,
    removeEntry: Function,
    useItem: Function
  },
  computed: {
    flour: function() {
      return this.getProportion(220);
    },
    water: function() {
      return this.getProportion(160);
    },
    total: function() {
      return this.entry.val + this.flour + this.water;
    }
  },
  methods: {
    getProportion(amount) {
      return Math.floor((this.entry.val / 300) * amount);
    }
  }
};
</script>

<style lang="sass" scoped>
button
    width: 40px
    height: 40px
    margin-left: 1em
    --webkit-appearance: none;
    background: #Eee
    border: none;
    border-radius: 100px
    cursor: pointer
    &.add
        background-color: #82eaef
    &.remove
        background-color: #ffd55f
td
    padding: .5em 1em
</style>
