<template>
  <div id="app">
    <form-wizard @on-complete="onComplete">
      <tab-content title="Personal details" icon="ti-user">
        My first tab content
      </tab-content>
      <tab-content title="Additional Info" icon="ti-settings">
        My second tab content
      </tab-content>
      <tab-content title="Last step" icon="ti-check">
        Yuhuuu! This seems pretty damn simple
      </tab-content>
      <template
        slot="footer"
        slot-scope="{
          activeTabIndex,
          isLastStep,
          nextTab,
          prevTab,
          fillButtonStyle
        }"
      >
        <div class="wizard-footer-left">
          <button
            v-if="activeTabIndex > 0"
            @click="prevTab"
            type="button"
            class="btn btn-outline-info"
          >
            Back
          </button>
        </div>
        <div class="wizard-footer-right">
          <button
            v-if="!isLastStep"
            @click="nextTab"
            type="button"
            class="btn btn-outline-success wizard-footer-right"
          >
            Next
          </button>

          <button
            v-else
            @click="nextTab"
            type="button"
            class="btn btn-danger btn-lg hello"
          >
            Finish
          </button>
        </div>
      </template>
    </form-wizard>
  </div>
</template>

<script>
export default {
  name: "app",
  methods: {
    onComplete: function() {
      alert("Yay. Done!");
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.hello {
  cursor: pointer;
}
</style>
