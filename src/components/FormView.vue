<template>
  <div id="form">
    <h1>Form</h1>
    <b-form @submit="onSubmit" @reset="onReset">
      <b-container>
        <b-row>
          <div class="col-md-6">
            <b-form-input
              id="input-1"
              v-model="form.fname"
              type="text"
              placeholder="Enter First Name"
              required
            ></b-form-input>
          </div>
          <div class="col-md-6">
            <b-form-input
              id="input-1"
              v-model="form.lname"
              type="text"
              placeholder="Enter Last Name"
              required
            ></b-form-input>
          </div>
        </b-row>
        &nbsp;
        <b-row>
          <div class="col-md-6">
            <b-form-input
              id="input-1"
              v-model="form.email"
              type="email"
              placeholder="Enter Email"
              required
            ></b-form-input>
          </div>
          <div class="col-md-6">
            <b-form-input
              id="input-1"
              v-model="form.mobile"
              type="text"
              placeholder="Enter Mobile"
              required
            ></b-form-input>
          </div>
        </b-row>
        &nbsp;
        <b-row>
          <div class="col-md-6">
            <b-form-select v-model="menuSelected" class="form-control">
              <option value="">Select a Continent</option>
              <option
                v-for="(userCountry_obj, userCountry) in userplaces"
                :key="userCountry"
              >
                {{ userCountry }}
              </option>
            </b-form-select>
          </div>
          <div class="col-md-6">
            <b-form-select
              v-model="selecteduserCountry"
              :disabled="userCountries.length == 0"
              class="form-control"
            >
              <option value="">Select a Country</option>
              <option
                v-for="(userCity_obj, userCity) in userCountries"
                :key="userCity"
              >
                {{ userCity }}
              </option>
            </b-form-select>
          </div>
        </b-row>
        &nbsp;
        <b-row>
          <div class="col-md-6">
            <b-form-select
              :disabled="userCities.length == 0"
              v-model="selecteduserCity"
              class="form-control"
            >
              <option value="">Select a City</option>
              <option v-for="userCity in userCities" :key="userCity">
                {{ userCity }}
              </option>
            </b-form-select>
          </div>
          <div class="col-md-6">
            <b-button type="submit" variant="primary">Submit</b-button>
            <b-button type="reset" variant="danger">Reset</b-button>
          </div>
        </b-row>

        <!-- <b-card class="mt-3" header="Form Data Result">
          <pre class="m-0">{{ form }}</pre>
        </b-card> -->
      </b-container>
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        fname: "",
        lname: "",
        email: "",
        mobile: "",
        show: true,
      },

      data: "kishore",
      name: "",
      email: "",
      userplaces: {
        Asia: {
          China: ["China 1", "China 2", "China 3", "China 4"],
          India: ["Delhi", "Goa", "Hyderabad", "Andhra Pradesh"],
          Japan: ["Japan 1", "Japan 2", "Japan 3", "Japan 4"],
          Singapore: ["Singapore 1"],
          Malaysia: ["Malaysia 1", "Malaysia 2", "Malaysia 3", "Malaysia 4"],
        },
        Europe: {
          Germany: [
            "Germany 1",
            "Germany 2",
            "Germany 3",
            "Germany 4",
            "Germany 5",
            "Germany 6",
          ],
          UK: ["UK 1", "UK 2", "UK 3", "UK 4"],
          France: ["France 1", "France 2", "France 3", "France 4"],
        },
      },
      userCountries: [],
      userCities: [],
      menuSelected: "",
      selecteduserCountry: "",
      selecteduserCity: "",
    };
  },
  watch: {
    menuSelected: function () {
      // Clear previously selected values
      this.userCountries = [];
      this.userCities = [];
      this.selecteduserCountry = "";
      this.selecteduserCity = "";
      // Populate list of userCountries in the second dropdown
      if (this.menuSelected.length > 0) {
        this.userCountries = this.userplaces[this.menuSelected];
      }
    },
    selecteduserCountry: function () {
      // Clear previously selected values
      this.userCities = [];
      this.selecteduserCity = "";
      // Now we have a continent and userCountry. Populate list of userCities in the third dropdown
      if (this.selecteduserCountry.length > 0) {
        this.userCities =
          this.userplaces[this.menuSelected][this.selecteduserCountry];
      }
    },
  },
  methods: {
    onSubmit(event) {
      event.preventDefault();
      alert(JSON.stringify(this.form));
    },
    onReset(event) {
      event.preventDefault();
      this.show = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.dropdown {
  margin: 10px 0;
  padding: 10px 0;
  border-bottom: 1px solid #ddd;
}

.dropdown span {
  display: inline-block;
  width: 80px;
}
</style>
