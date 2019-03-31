<template>
  <card :title="table1.title">
    <div class="table-responsive">
      <base-table :data="table1.data"
                  :columns="table1.columns"
                  thead-classes="text-primary">
      </base-table>
    </div>
  </card>
</template>

<script>
  import { BaseTable } from "@/components";
  const tableColumns = ["Name", "Actions"];
  const tableData = [
    {
      id: 1,
      name: "Carrefour",
    },
    {
      id: 2,
      name: "Auchan",
    },
    {
      id: 3,
      name: "Magazinul de la colt",
    },
  ];

	export default {
		name: "CustomersList",
    components: {BaseTable},
    data() {
      return {
        table1: {
          title: "Customer List",
          columns: [...tableColumns],
          data: [...tableData]
        }
      };
    }
	}
</script>

<style scoped>

</style>
