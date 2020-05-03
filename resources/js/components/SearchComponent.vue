<template>
<div>
    <br>
    <div class="level">
    <div class="level-item">
        <h5 class="heading">Procure por um País</h5>
    </div>
    </div>

     <div class="level">
    <div class="level-item">
        <div class="field has-addons">
    <div class="control">
        <input class="input" type="text" placeholder="Ex: Portugal">
    </div>
    <div class="control">
        <button class="button is-info" @click="searchCountry()">
        Procurar
        </button>
    </div>
    </div>
    </div>

</div>

  <div class="columns" v-if="search">
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

  </div>

</template>

<script>
import axios  from 'axios';
export default {
  data() {
    return {
      search: false,
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
  },
  methods: {
      searchCountry() {
        this.search = true,
        console.log("Ola");

      }
  }
};
</script>

<style>
</style>
