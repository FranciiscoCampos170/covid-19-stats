<template>
  <h1>{{ stats }}</h1>
</template>

<script>
import axios  from 'axios';
export default {
  data() {
    return {
      stats: [],
      errors: [],
      url: "https://corona.lmao.ninja/v2/all"
    };
  },
  mounted() {
      axios.get(this.url)
      .then(response => {
          this.stats = response.data
      }).catch(e => {
          this.errors.push(e)
      })

  }
};
</script>

<style>
</style>
