<template>
  <card :title="table.title">
    <div class="col-md-3 px-md-3">
      <base-input label="Service">
        <select class="form-control" id="serviceSelect" v-model="selectedService">
          <option v-for="service in services" :value="service.id">{{ service.name }}</option>
        </select>
      </base-input>
    </div>
    <div class="table-responsive">
      <base-table :data="table.data"
                  :columns="table.columns"
                  thead-classes="text-primary">
      </base-table>
    </div>
  </card>
</template>

<script>
  import { BaseTable } from "@/components";
  const tableColumns = ["Name", "Service", "Method", "API URL", "Actions"];

  export default {
    name: "MetricsList",
    components: {BaseTable},
    data() {
      return {
        table: {
          title: "Metrics List",
          columns: [...tableColumns],
          data: []
        },
        services: [],
        selectedService: 0
      };
    },
    mounted() {
      this.axios.post('http://localhost:8000/service/list').then(response => {
        this.services = response.data;
      })
    },
    watch: {
      selectedService: function (val, oldVal) {
        this.reload(val);
      }
    },
    methods: {
      reload (service) {
        this.axios.post('http://localhost:8000/metric/list/' + service).then(response => {
          this.table.data = response.data;
        })
      }
    }
  }
</script>

<style scoped>

</style>
