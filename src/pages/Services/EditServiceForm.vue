<template>
  <card :title="title">
    <form @submit.prevent>
      <div class="row">
        <div class="col-md-6 px-md-3">
          <base-input label="Name" placeholder="Type service name" v-model="service.name"/>
        </div>
        <div class="col-md-3 px-md-3">
          <base-button native-type="submit" type="success" @click="saveService">Submit</base-button>
        </div>
        <div class="col-md-3 px-md-3">
          <base-button native-type="reset" type="primary">Reset</base-button>
        </div>
      </div>
    </form>
  </card>
</template>

<script>
  import ServiceAddNotification from "../Notifications/ServiceAddNotification";

  const ADD_TITLE = "Add Service";
  const EDIT_TITLE = "Edit Service";
  let apiConfig = {
    headers: {
      'Content-Type': 'application/json'
    }
  };

  export default {
    name: "EditServiceForm",
    data() {
      return {
        title: ADD_TITLE,
        service: {
          type: Object,
          default: () => {
            return {};
          }
        }
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
      },
      saveService(event) {
        this.axios.post('http://localhost:8000/service/add', this.service, apiConfig).then(response => {
          if (response.data) {
            this.service = {};
            this.$emit('add');
            this.$notify({
              component: ServiceAddNotification,
              icon: "tim-icons icon-check-2",
              horizontalAlign: "center",
              verticalAlign: "top",
              type: "success",
              timeout: 0
            });
          }
        })
      }
    }
  }
</script>

<style scoped>

</style>
