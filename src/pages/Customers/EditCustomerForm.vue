<template>
  <card :title="title">
    <form @submit.prevent>
      <div class="row">
        <div class="col-md-6 px-md-3">
          <base-input label="Name" placeholder="Type customer name"/>
        </div>
        <div class="col-md-3 px-md-3">
          <base-button native-type="submit" type="success">Submit</base-button>
        </div>
        <div class="col-md-3 px-md-3">
          <base-button native-type="reset" type="primary">Reset</base-button>
        </div>
      </div>
    </form>
  </card>
</template>

<script>
  const ADD_TITLE = "Add Service";
  const EDIT_TITLE = "Edit Service";

	export default {
		name: "EditCustomerForm",
    data() {
      return {
        title: ADD_TITLE,
      }
    },
    mounted() {
    },
    methods: {
      setAddMode () {
        this.title = ADD_TITLE;
      },
      setEditMode () {
        this.title = EDIT_TITLE;
      }
    }
	}
</script>

<style scoped>

</style>
