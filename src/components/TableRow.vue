<template>
  <tr @click="showTaskBar">
    <td>{{ renewal.bond_number }}</td>
    <td>{{ renewal.principal_name }}</td>
    <td>{{ renewal.status }}</td>
  </tr>
</template>

<script>
import sharedState from "../sharedState";

export default {
  name: "TableRow",
  data() {
    return {
      sharedState: sharedState
    };
  },
  props: ["renewal"],
  methods: {
    showTaskBar() {
      this.sharedState.showTaskBar = true;
      this.sharedState.currentRenewal = this.renewal;
    }
  }
};
</script>

<style></style>
