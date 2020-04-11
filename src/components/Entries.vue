<template>
  <div>
    <button @click="addEntry">+ Save weight</button>
    <div class="entries"></div>
    <table>
      <thead>
        <tr>
          <th>Levain</th>
          <th>Flour</th>
          <th>Water</th>
          <th>Total weight</th>
          <td></td>
        </tr>
      </thead>
      <tbody>
        <Entry
          v-for="entry in entries"
          :key="entry.date"
          :entry="entry"
          :removeEntry="removeEntry"
          :useItem="setAvailableLevain"
        />
      </tbody>
    </table>
  </div>
</template>

<script>
import Entry from "./Entry";
export default {
  name: "Entries",
  components: { Entry },
  props: {
    currentLevainAmount: Number,
    setAvailableLevain: Function
  },
  mounted() {
    if (localStorage.entries && localStorage.entries.length > 0) {
      this.entries = JSON.parse(localStorage.entries);
    }
  },
  data: function() {
    return {
      entries: []
    };
  },
  watch: {
    entries(newEntries) {
      localStorage.entries = JSON.stringify(newEntries);
    }
  },
  methods: {
    addEntry() {
      const now = new Date().getTime();
      const newEntry = {
        val: this.currentLevainAmount,
        date: now
      };
      this.entries = [newEntry, ...this.entries];
    },
    removeEntry(key) {
      this.entries = this.entries.filter(item => item.date !== key);
    }
  }
};
</script>

<style scoped lang="sass">
button
    transition: all 200ms
    background-color: #fff
    -webkit-appearance: none
    display: block
    font-size: 1rem
    cursor: pointer
    border-radius: 5px
    padding: .5em 2em;
    margin-top: 1em
    border: 3px #ddd solid
    box-shadow: none
    margin: 10px auto
    text-transform: uppercase

    &:hover
        border-color: #bbb
table
    table-colapse: colapse
    width: 100%
tr
    border-bottom: 1px solid #ccc
th
    padding: .5em 1em
</style>
