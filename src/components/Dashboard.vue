<template>
  <div>
    <h1>Dashboard</h1>
    <div class="companyBox">
      <Company v-for="company in companies" :key="company.id" v-bind:name="company.name" v-bind:stock="company.stock" />
    </div>
  </div>
</template>

<script>
import Company from "./Company";
import SocketIOClient from "socket.io-client";

const socket = SocketIOClient.connect("http://localhost:3001");

export default {
  name: "Dashboard",
  components: {
    Company,
  },
  data() {
    return {
      companies: [],
    };
  },
  beforeMount() {
    this.getName();
  },
  created() {
    socket.on("newStockValues", (data) => {
      const companiesLatestUpdated = this.companies.map((comp) => {
        const dataForThisComp = data.find((d) => d.id === comp.id);
        if (dataForThisComp) {
          return dataForThisComp;
        } else {
          return comp;
        }
      });
      this.companies = companiesLatestUpdated;
    });
  },
  beforeDestroy() {
    socket.close();
  },
  methods: {
    async getName() {
      const res = await fetch("http://localhost:3001/companies");
      const data = await res.json();
      this.companies = data;
    },
  },
};
</script>

<style scoped>
.companyBox {
  display: flex;
  flex-wrap: wrap;
}
</style>
