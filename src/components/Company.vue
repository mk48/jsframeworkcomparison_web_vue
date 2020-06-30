<template>
  <div class="company">
    <div>{{ name }}</div>
    <div>{{ stock }}</div>
  </div>
</template>

<script>
export default {
  name: "Company",
  props: {
    name: String,
    stock: Number,
  },
};
</script>

<style scoped>
.company {
  width: 70px;
  height: 45px;
  background-color: lightsteelblue;
  margin: 2px;
  padding: 2px;
}
</style>
