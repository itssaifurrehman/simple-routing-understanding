<template>
  <div v-if="job">
    <h1>Job ID: {{ id }}</h1>
    <p>Job Title: {{ job.title }}</p>
    <p>Job Description: {{ job.details }}</p>
  </div>
  <div v-else><p>Data is being loaded, Please wait!</p></div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      job: null,
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => {
        this.job = data;
        console.log(this.job);
      })
      .catch((err) => console.log(err.message));
  },
  // data() {
  //   return {
  //     id: this.$route.params.id
  //   }
  // }
};
</script>

<style>
</style>