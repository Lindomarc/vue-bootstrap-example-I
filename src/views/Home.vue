<template>
<b-container class="bv-example-row">
  
  <b-row align-v="center">

    <job-card v-for="job in displayJobs" :key="job.id" :name="job.name"></job-card>
   
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

export default {
  name: "Home",
  data(){
    return {
      jobs:[],
      displayJobs:[],
      rows: 1,
      currentPage:1,
      perPage: 3
    }
  },
  components: {
     "job-card": JobCard  
  },
  mounted() {
    this.fetchData();
  },
  methods:{
    async fetchData(){
      const res = await fetch("jobs.json");
      const val = await res.json();
      this.jobs = val;
      this.displayJobs = val.slice(0,3);
      this.rows = val.length
      
    },
    paginate(currentPage){
      const start = (currentPage - 1) * this.perPage;
      this.displayJobs = this.jobs.slice(start,  start+3)
    }
  }
};
</script>
