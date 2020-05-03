<template>
  <b-container>
    <b-row align-v="center">
      <JobCard v-for="job in jobs" :key="job.id" :name="job.name" />
    </b-row>
  </b-container>
</template>

<script>
// @ is an alias to /src
import JobCard from "@/components/JobCard.vue";

export default {
  name: "Home",
  components: {
    JobCard
  },
  data: () => ({
    jobs: []
  }),
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const res = await fetch("jobs.json");
      const val = await res.json();
      this.jobs = val;
    }
  }
};
</script>
