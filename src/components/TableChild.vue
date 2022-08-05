<template>
  <div>
    <div class="row">
      <div class="col-md-6">
        <table>
          <thead>
            <th>Name</th>
            <th>Email</th>
          </thead>
          <tbody>
            <tr v-for="(spec, index) in user_data" :key="index">
              <th>{{ spec.name }}</th>
              <th>{{ spec.email }}</th>
              <th>
                <b-button variant="danger" v-if="spec.status === 'error'"
                  >Button</b-button
                >
                <b-button
                  variant="success"
                  v-else-if="spec.status === 'success'"
                  >Button</b-button
                >
                <b-button
                  variant="primary"
                  v-else-if="spec.status === 'primary'"
                  >Button</b-button
                >
              </th>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col-md-6">
        <table>
          <thead>
            <th>Name</th>
            <th>Email</th>
          </thead>
          <tbody>
            <tr v-for="(spec, index) in user_data" :key="index">
              <th>{{ spec.name }}</th>
              <th>{{ spec.email }}</th>
              <th>
                <b-button :variant="status(spec.status)" @click="showModal(spec)">{{spec.status }}</b-button>
              </th>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <b-modal ref="modalOpen" hide-footer title="Using Component Methods">
      <div class="d-block text-center">
        <h3>Modal!</h3>
         <table>
          <thead>
            <th>Name</th>
            <th>Email</th>
            <th>Status</th>
          </thead>
          <tbody>
          
              <th>{{ popupdata.name }}</th>
              <th>{{ popupdata.email }}</th>
              <th>
                <b-button :variant="status(popupdata.status)">{{popupdata.status }}</b-button>
              </th>
          </tbody>
        </table>
      </div>
    </b-modal>
  </div>
</template>

<script>
export default {
  name: "TableComponent",
  props: ["user_data"],
  data() {
    return {
        popupdata: '',
    }
  },
  methods: {
    status(id) {
      if (id == "success") {
        return "success";
      } else if (id == "primary") {
        return "primary";
      } else if (id == "error") {
        return "danger";
      }
    },
    showModal(val) {
      console.log(val);
      this.popupdata=val; 
      this.$refs["modalOpen"].show();
    },
    hideModal(ids) {
      console.log(ids);
      this.$refs["modalOpen"].hide();
    },
    toggleModal() {
      this.$refs["modalOpen"].toggle("#toggle-btn");
    },
  },
};
</script>

