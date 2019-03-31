<template>
  <div class="row">
    <div class="col-md-6">
      <edit-service-form v-on:add="triggerReload"/>
    </div>
    <div class="col-md-6">
      <services-list ref="list"></services-list>
    </div>
  </div>
</template>

<script>
  import EditServiceForm from "./Services/EditServiceForm";
  import ServicesList from "./Services/ServicesList";

  export default {
    name: "Services",
    components: {ServicesList, EditServiceForm},
    methods: {
      triggerReload() {
        this.$refs.list.reload();
      }
    }
  }
</script>

<style scoped>

</style>
