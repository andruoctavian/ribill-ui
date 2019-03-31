<template>
  <div class="row">
    <div class="col-md-12">
      <edit-metric-form v-on:add="triggerReload"/>
    </div>
    <div class="col-md-12">
      <metrics-list  ref="list" />
    </div>
  </div>
</template>

<script>
  import EditMetricForm from "./Metrics/EditMetricForm";
  import MetricsList from "./Metrics/MetricsList";
  export default {
    name: "Metrics",
    components: {MetricsList, EditMetricForm},
    methods: {
      triggerReload(service) {
        this.$refs.list.reload(service);
        this.$refs.list.selectedService = service;
      }
    }
  }
</script>

<style scoped>

</style>
