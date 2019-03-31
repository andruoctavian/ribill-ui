<template>
  <div class="row">
    <div class="col-md-6">
      <edit-customer-form :model="model" />
    </div>
    <div class="col-md-6">
      <customers-list :user="user"></customers-list>
    </div>
    <!--<div class="col-12">-->
      <!--<card :title="table1.title">-->
        <!--<div class="table-responsive">-->
          <!--<base-table :data="table1.data"-->
                      <!--:columns="table1.columns"-->
                      <!--thead-classes="text-primary">-->
          <!--</base-table>-->
        <!--</div>-->
      <!--</card>-->
    <!--</div>-->
  </div>
</template>

<script>
  import { BaseTable } from "@/components";
  import EditCustomerForm from "./Customers/EditCustomerForm";
  import CustomersList from "./Customers/CustomersList";
  const tableColumns = ["Name", "Country", "City", "Salary"];
  const tableData = [
    {
      id: 1,
      name: "Dakota Rice",
      salary: "$36.738",
      country: "Niger",
      city: "Oud-Turnhout",
    },
    {
      id: 2,
      name: "Minerva Hooper",
      salary: "$23,789",
      country: "Curaçao",
      city: "Sinaai-Waas"
    },
    {
      id: 3,
      name: "Sage Rodriguez",
      salary: "$56,142",
      country: "Netherlands",
      city: "Baileux"
    },
    {
      id: 4,
      name: "Philip Chaney",
      salary: "$38,735",
      country: "Korea, South",
      city: "Overland Park"
    },
    {
      id: 5,
      name: "Doris Greene",
      salary: "$63,542",
      country: "Malawi",
      city: "Feldkirchen in Kärnten"
    },
    {
      id: 6,
      name: 'Mason Porter',
      salary: '$98,615',
      country: 'Chile',
      city: 'Gloucester'
    },
    {
      id: 7,
      name: 'Jon Porter',
      salary: '$78,615',
      country: 'Portugal',
      city: 'Gloucester'
    }
  ];

  export default {
    name: "Customers",
    components: {CustomersList, EditCustomerForm, BaseTable},
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
