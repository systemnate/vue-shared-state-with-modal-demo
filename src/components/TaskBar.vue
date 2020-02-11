<template>
  <div v-if="sharedState.showTaskBar">
    <transition name="modal">
      <div class="modal-mask">
        <div class="modal-wrapper">
          <div class="modal-dialog" role="document">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title">Modal title</h5>
                <button
                  type="button"
                  class="close"
                  data-dismiss="modal"
                  aria-label="Close"
                >
                  <span aria-hidden="true" @click="closeModal">&times;</span>
                </button>
              </div>
              <div class="modal-body">
                <table class="table">
                  <thead>
                    <th>Bond Number</th>
                    <th>Principal Name</th>
                    <th>Status</th>
                  </thead>
                  <tbody>
                    <tr>
                      <td>{{ sharedState.currentRenewal.bond_number }}</td>
                      <td>{{ sharedState.currentRenewal.principal_name }}</td>
                      <td>{{ sharedState.currentRenewal.status }}</td>
                    </tr>
                  </tbody>
                </table>
              </div>
              <div class="modal-footer">
                <button
                  type="button"
                  class="btn btn-secondary"
                  @click="closeModal"
                >
                  Close
                </button>
                <button
                  @click="markReviewed"
                  type="button"
                  class="btn btn-primary"
                >
                  Mark as Reviewed
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import sharedState from "../sharedState";

export default {
  name: "TaskBar",
  data() {
    return {
      sharedState: sharedState
    };
  },
  methods: {
    closeModal() {
      this.sharedState.showTaskBar = false;
    },
    markReviewed() {
      const renewal = this.sharedState.renewals.find(
        renewal => renewal.id === this.sharedState.currentRenewal.id
      );
      renewal.status = "Reviewed";
    }
  }
};
</script>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}
</style>
