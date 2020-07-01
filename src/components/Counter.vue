<template>
  <div id="counter">
    {{ value }}
    <button v-on:click="increment">+</button>
    <button v-on:click="decrement">-</button>
  </div>
</template>

<script>
export default {
  name: "Counter",
  data() {
    return {
      value: 0,
    };
  },
  methods: {
    increment: function() {
      this.value += 1;
    },
    decrement: function() {
      this.value -= 1;
    },
  },
};
</script>
