<template>
  <div class="root">
    <div class="pre-title">{{ label }}</div>
    <div class="title">{{ amount }}</div>
  </div>
</template>

<script>
export default {
  name: "ValueDisplay",
  props: {
    label: String,
    amount: Number
  }
};
</script>

<style lang="scss">
.root {
  text-align: center;
  padding: 1rem;
  border: solid #eee 1px;
  border-radius: 2px;
  width: 100%;
}
.pre-title {
  text-transform: uppercase;
}
.title {
  transition: all 600ms;
  font-size: 14vw;
  font-weight: 900;
  margin: 0;
  margin-top: 5px;
  @media screen and (min-width: 800px) {
    font-size: 10rem;
  }
}
</style>
