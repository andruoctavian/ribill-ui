<template>
  <card :title="table.title">
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
  const tableColumns = ["Name", "Actions"];

  export default {
    name: "ServicesList",
    components: {BaseTable},
    data() {
      return {
        table: {
          title: "Services List",
          columns: [...tableColumns],
          data: []
        }
      };
    },
    mounted() {
      this.reload();
    },
    methods: {
      reload () {
        this.axios.post('http://localhost:8000/service/list').then(response => {
          this.table.data = response.data;
        })
      }
    }
  }
</script>

<style scoped>

</style>
