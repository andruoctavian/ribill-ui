<template>
	<card :title="title">
    <form @submit.prevent>
      <div class="row">
        <div class="col-md-3 px-md-3">
          <base-input label="Name" placeholder="Type metric name" v-model="metric.name"/>
        </div>
        <div class="col-md-3 px-md-3">
          <base-input label="Service">
            <select class="form-control" id="serviceSelect" v-model="metric.serviceId">
              <option v-for="service in services" :value="service.id">{{ service.name }}</option>
            </select>
          </base-input>
        </div>
      </div>
      <div class="row">
        <div class="col-md-3 px-md-3">
          <base-input label="Method">
            <select class="form-control" id="selectMethod" v-model="metric.method">
              <option value="GET">GET</option>
              <option value="POST">POST</option>
              <option value="PUT">PUT</option>
              <option value="DELETE">DELETE</option>
            </select>
          </base-input>
        </div>
        <div class="col-md-9 px-md-3">
          <base-input label="API URL" placeholder="Type metric API URL" v-model="metric.apiUrl"/>
        </div>
      </div>
      <div class="row">
        <div class="col-md-3 px-md-3">
          <base-button native-type="reset" type="primary">Reset</base-button>
        </div>
        <div class="col-md-3 px-md-3">
          <base-button native-type="submit" type="success" @click="saveMetric">Submit</base-button>
        </div>
      </div>
    </form>
  </card>
</template>

<script>
  import MetricAddNotification from "../Notifications/MetricAddNotification";

  const ADD_TITLE = "Add Metric";
  const EDIT_TITLE = "Edit Metric";
  let apiConfig = {
    headers: {
      'Content-Type': 'application/json'
    }
  };

	export default {
		name: "EditMetricForm",
    components: {},

    data() {
      return {
        title: ADD_TITLE,
        metric: {
          type: Object,
          default: () => {
            return {};
          }
        },
        services: [],
      }
    },
    mounted() {
      this.axios.post('http://localhost:8000/service/list').then(response => {
        this.services = response.data;
      })
    },
    methods: {
      setAddMode () {
        this.title = ADD_TITLE;
      },
      setEditMode () {
        this.title = EDIT_TITLE;
      },
      saveMetric(event) {
        let serviceId = this.metric.serviceId;
        this.axios.post('http://localhost:8000/metric/add/' + serviceId, this.metric, apiConfig).then(response => {
          if (response.data) {
            this.$emit('add', serviceId);
            this.metric = {};
            this.$notify({
              component: MetricAddNotification,
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
