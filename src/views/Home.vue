<template>
  <b-container>
    <b-row align-v="center">
      <JobCard
        v-for="job in displayJobs"
        :key="job.id"
        :name="job.name"
        :id="job.id"
      />
    </b-row>
    <b-pagination
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      first-text="First"
      prev-text="Prev"
      next-text="Next"
      last-text="Last"
      @input="paginate(currentPage)"
    ></b-pagination>
  </b-container>
</template>

<script>
// @ is an alias to /src
import JobCard from "@/components/JobCard.vue";
import { mapGetters } from "vuex";

export default {
  name: "Home",
  components: {
    JobCard
  },
  computed: {
    ...mapGetters(["jobs", "displayJobs", "rows"])
  },
  data: () => ({
    currentPage: 1,
    perPage: 3
  }),
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      await this.$store.dispatch("fetchJobs");
    },
    paginate(currentPage) {
      this.$store.dispatch("paginate", { currentPage, perPage: this.perPage });
    }
  }
};
</script>
