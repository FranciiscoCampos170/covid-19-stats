<template>
<div>



<h3>Global</h3>
  <div class="columns">
      <div class="column">
          <p>{{ stats.todayCases.toFixed() }}</p>
          <p>Casos de Hoje</p>
      </div>
      <div class="column">
          <p>{{stats.todayDeaths}}</p>
          <p>Mortes de Hoje</p>
      </div>
      <div class="column">
          <p>{{stats.cases}}</p>
          <p>Total de Casos</p>
      </div>
      <div class="column">
          <p>{{stats.deaths}}</p>
          <p>Total de Mortes</p>
      </div>
  </div>

<div class="columns">
  <div class="column">
          <p>{{ stats.active }}</p>
          <p>Total Casos de Activos</p>
      </div>
      <div class="column">
          <p>{{ stats.critical }}</p>
          <p>Total Estado Crítico</p>
      </div>
      <div class="column">
          <p>{{ stats.recovered }}</p>
          <p>Total de Recuperados</p>
      </div>
      <div class="column">
          <p>{{ stats.tests }}</p>
          <p>Total de Testes Feitos</p>
      </div>
  </div>

</div>
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
          console.log(this.stats);

      }).catch(e => {
          this.errors.push(e)
      })

  }
};
</script>

<style>
</style>
