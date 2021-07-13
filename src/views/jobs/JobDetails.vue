<template>

<div v-if="job">
  <h1>{{ job.title }}</h1>
  <p>The job id is {{ id }}</p>
  <p>{{ job.details }}</p>
</div>
<div v-else>
  <p>Loading job details...</p>
</div>
  
</template>

<script>
export default {
	props: ['id'],
  data () {
    return {
      job: null
    }
  },
  mounted() {
    // to see it on other devices than on your machine
    // write your IPv4 address so it matches the
    // default is localhost for json-server
    // run 'npx json-server --watch -H localhost -P 3000 data/db.json' for localhost access only
    // run 'npx json-server --watch -H [YourIPv4] -P 3000 data/db.json' for Networked access
      fetch('http://localhost:3000/jobs/' + this.id)
      .then(res => res.json())
      .then(data => this.job = data)
      .catch(err => console.log(err.message))
    }
}
</script>

<style>

</style>