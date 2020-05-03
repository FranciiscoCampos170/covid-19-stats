<template>
<div>
<div class="level">
    <div class="level-item">
        <br>
    <h3 class="heading">Em Angola</h3>
    </div>
</div>

  <div class="columns">
      <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{ stats.todayCases }}</strong>
                <br>
                Casos de Hoje
                </p>
            </div>
            </div>
        </article>
        </div>
      </div>

        <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{stats.todayDeaths}}</strong>
                <br>
                Mortes de Hoje
                </p>
            </div>
            </div>
        </article>
        </div>
      </div>

      <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{stats.cases}}</strong>
                <br>
                Total de Casos
                </p>
            </div>
            </div>
        </article>
        </div>
      </div>

      <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{stats.deaths}}</strong>
                <br>
                Total de Mortes
                </p>
            </div>
            </div>
        </article>
        </div>
      </div>

  </div>

<div class="columns">
    <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{ stats.active }}</strong>
                <br>
                Total Casos de Activos
                </p>
            </div>
            </div>
        </article>
        </div>
      </div>

      <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{ stats.critical }}</strong>
                <br>
                Total Estado Crítico
                </p>
            </div>
            </div>
        </article>
        </div>
      </div>

      <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{ stats.recovered }}</strong>
                <br>
                Total de Recuperados
                </p>
            </div>
            </div>
        </article>
        </div>
      </div>

      <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{ stats.tests }}</strong>
                <br>
                Total de Testes Feitos
                </p>
            </div>
            </div>
        </article>
        </div>
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
      url: "https://corona.lmao.ninja/v2/countries/Angola"
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
