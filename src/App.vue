<template>
  <div id="app">
    <Counter />
    <Dashboard />
  </div>
</template>

<script>
import Dashboard from "./components/Dashboard.vue";
import Counter from "./components/Counter.vue";

export default {
  name: "App",
  components: {
    Dashboard,
    Counter,
  },
};
</script>
