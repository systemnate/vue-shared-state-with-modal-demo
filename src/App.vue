<template>
  <div>
    <task-bar :renewal="sharedState.currentRenewal"></task-bar>
    <table class="table">
      <thead>
        <th>Bond Number</th>
        <th>Principal Name</th>
        <th>Status</th>
      </thead>
      <tbody>
        <table-row
          v-for="renewal in sharedState.renewals"
          :renewal="renewal"
          :key="renewal.id"
        ></table-row>
      </tbody>
    </table>
  </div>
</template>

<script>
import TableRow from "./components/TableRow.vue";
import TaskBar from "./components/TaskBar.vue";
import sharedState from "./sharedState";

export default {
  name: "App",
  components: {
    "table-row": TableRow,
    "task-bar": TaskBar
  },
  data() {
    return {
      sharedState: sharedState
    };
  }
};
</script>

<style></style>
