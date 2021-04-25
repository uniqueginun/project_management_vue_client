<template>
  <div>
    <!-- Page Heading -->
    <div class="d-sm-flex align-items-center justify-content-between mb-4">
      <h1 class="h3 mb-0 text-gray-800">Create Project</h1>
    </div>

    <!-- Content Row -->

    <div class="row">
      <!-- Area Chart -->
      <div class="col-12">
        <div class="card shadow mb-4">
          <div class="card-body">
            <form class="user" @submit.prevent="createProject">
              <div class="form-group">
                <label for="projectName">Project Name</label>
                <input
                  type="text"
                  class="form-control"
                  id="projectName"
                  v-model="project.name"
                  :class="{ 'is-invalid': errors.hasOwnProperty('name') }"
                />
                <div
                  class="invalid-feedback"
                  v-if="errors.hasOwnProperty('name')"
                >
                  {{ errors.name[0] }}
                </div>
              </div>
              <div class="form-group row">
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="projectCity">Project City</label>
                  <select
                    class="custom-select"
                    id="projectCity"
                    v-model="project.city"
                    :class="{ 'is-invalid': errors.hasOwnProperty('city') }"
                  >
                    <option value="">select city</option>
                    <option
                      v-for="(city, index) in cities"
                      :key="index"
                      :value="city.id"
                    >
                      {{ city.name }}
                    </option>
                  </select>
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('city')"
                  >
                    {{ errors.city[0] }}
                  </div>
                </div>
                <div class="col-sm-6">
                  <label for="projectContractor">Project Contractor</label>
                  <select
                    class="custom-select"
                    id="projectContractor"
                    v-model="project.contractor"
                    :class="{
                      'is-invalid': errors.hasOwnProperty('contractor'),
                    }"
                  >
                    <option value="">select contractor</option>
                    <option
                      v-for="(contractor, index) in contractors"
                      :key="index"
                      :value="contractor.id"
                    >
                      {{ contractor.name }}
                    </option>
                  </select>
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('contractor')"
                  >
                    {{ errors.contractor[0] }}
                  </div>
                </div>
              </div>
              <div class="form-group row">
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="projectStart">Start date</label>
                  <input
                    type="text"
                    class="form-control"
                    id="projectStart"
                    v-model="project.start"
                    :class="{ 'is-invalid': errors.hasOwnProperty('start') }"
                  />
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('start')"
                  >
                    {{ errors.start[0] }}
                  </div>
                </div>
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="projectEnd">End date</label>
                  <input
                    type="text"
                    class="form-control"
                    id="projectEnd"
                    v-model="project.end"
                    :class="{ 'is-invalid': errors.hasOwnProperty('end') }"
                  />
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('end')"
                  >
                    {{ errors.end[0] }}
                  </div>
                </div>
              </div>
              <div class="form-group row">
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="projectCost">Project cost</label>
                  <input
                    type="text"
                    class="form-control"
                    id="projectCost"
                    v-model="project.cost"
                    :class="{ 'is-invalid': errors.hasOwnProperty('cost') }"
                  />
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('cost')"
                  >
                    {{ errors.cost[0] }}
                  </div>
                </div>
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="projecPaid">Paid amount</label>
                  <input
                    type="text"
                    class="form-control"
                    id="projecPaid"
                    v-model="project.paid"
                    :class="{ 'is-invalid': errors.hasOwnProperty('paid') }"
                  />
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('paid')"
                  >
                    {{ errors.paid[0] }}
                  </div>
                </div>
              </div>
              <div class="form-group row">
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="projectPercentage">Project percentage</label>
                  <input
                    type="text"
                    class="form-control"
                    id="projectPercentage"
                    v-model="project.percentage"
                    :class="{
                      'is-invalid': errors.hasOwnProperty('percentage'),
                    }"
                  />
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('percentage')"
                  >
                    {{ errors.percentage[0] }}
                  </div>
                </div>
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="projecStatus">Project status</label>
                  <select
                    class="custom-select"
                    id="projecStatus"
                    v-model="project.status"
                    :class="{ 'is-invalid': errors.hasOwnProperty('status') }"
                  >
                    <option value="">select project current status</option>
                    <option
                      v-for="item in Object.keys(statuses)"
                      :key="item"
                      :value="item"
                    >
                      {{ statuses[item] }}
                    </option>
                  </select>
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('status')"
                  >
                    {{ errors.status[0] }}
                  </div>
                </div>
              </div>
              <div v-if="showStatusFields" class="form-group row">
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="statusDate">Date</label>
                  <input
                    type="text"
                    class="form-control"
                    id="statusDate"
                    v-model="project.status_date"
                    :required="showStatusFields"
                    :class="{
                      'is-invalid': errors.hasOwnProperty('status_date'),
                    }"
                  />
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('status_date')"
                  >
                    {{ errors.status_date[0] }}
                  </div>
                </div>
                <div class="col-sm-6 mb-3 mb-sm-0">
                  <label for="statusReason">Reason</label>
                  <input
                    type="text"
                    class="form-control"
                    id="statusReason"
                    v-model="project.status_reason"
                    :required="showStatusFields"
                    :class="{
                      'is-invalid': errors.hasOwnProperty('status_reason'),
                    }"
                  />
                  <div
                    class="invalid-feedback"
                    v-if="errors.hasOwnProperty('status_reason')"
                  >
                    {{ errors.status_reason[0] }}
                  </div>
                </div>
              </div>
              <button
                type="submit"
                :disabled="processing"
                class="btn btn-primary btn-user d-flex align-items-center justify-content-center"
              >
                <div class="font-weight-bolder">Create Project</div>
                <div
                  v-if="processing"
                  class="mx-3 spinner-border"
                  role="status"
                >
                  <span class="sr-only">Loading...</span>
                </div>
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: "default",
  middleware: ["auth", "moderator"],
  data() {
    return {
      errors: {},
      processing: false,
      project: {
        name: "",
        city: "",
        contractor: "",
        start: "",
        end: "",
        cost: "",
        paid: "",
        percentage: "",
        status: "",
        status_reason: "",
        status_date: "",
      },
    };
  },
  async asyncData({ $axios }) {
    const { data } = await $axios.get("api/data-lookups");
    return { ...data };
  },
  methods: {
    async createProject() {
      this.errors = {};
      this.processing = true;
      try {
        const { data } = await this.$axios.post("/api/projects", this.project);
        console.log(data);
      } catch (error) {
        const { data, status } = error.response;
        if (status === 422) {
          this.errors = data.errors;
        }
      }
      this.processing = false;
    },
  },
  computed: {
    showStatusFields() {
      return this.project.status && parseInt(this.project.status) !== 1;
    },
  },
};
</script>