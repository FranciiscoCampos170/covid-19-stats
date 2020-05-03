<template>
<div>
<div class="level">
    <div class="level-item">
        <br>
    <h3 class="heading">Todos</h3>
    </div>
</div>
<BulmaAccordion :dropdown="false" :icon="'custom'" v-for="stat in stats" :key="stat.countryInfo.id">
    <BulmaAccordionItem>
        <div slot="title" style="width:50px">
            <img :src="stat.countryInfo.flag">
        </div>
        <h4 slot="title" style="padding-left:10px;">{{ stat.country}}</h4>
        <i slot="icon-closed" class="material-icons">expandir</i>
        <i slot="icon-open" class="material-icons">ocultar</i>
        <p slot="content">
            <ul class="list is-hoverable">
                <li class="list-item" >Casos de Hoje: <strong>{{ stat.todayCases }}</strong></li>
                <li class="list-item" >Mortes de Hoje: <strong>{{stat.todayDeaths}}</strong></li>
                <li class="list-item" >Total de Casos: <strong>{{stat.cases}}</strong></li>
                <li class="list-item" >Total de Mortes: <strong>{{stat.deaths}}</strong></li>
                <li class="list-item" >Total Casos de Activos: <strong>{{ stat.active }}</strong></li>
                <li class="list-item" >Total Estado Crítico: <strong>{{ stat.critical }}</strong></li>
                <li class="list-item" >Total de Recuperados: <strong>{{ stat.recovered }}</strong></li>
            </ul>
        </p>
    </BulmaAccordionItem>
</BulmaAccordion>
  <!-- <div class="columns is-4" v-for="stat in stats" :key="stat.countryInfo.id">
      <div class="column">
          <div class="box">
        <article class="media">
            <div class="media-left">
                <figure class="image is-64x64">
                    <img :src="stat.countryInfo.flag" alt="Image">
                </figure>
            </div>
            <div class="media-content">
            <div class="content">
                <p class="has-text-centered">
                <strong>{{stat.country }}</strong>
                <br>
                </p>
            </div>
            </div>
        </article>
        </div>
      </div>



  </div> -->
</div>


</template>

<script>
import axios  from 'axios';
import { BulmaAccordion, BulmaAccordionItem } from 'vue-bulma-accordion'

export default {
  data() {
    return {
      stats: [],
      errors: [],
      url: "https://corona.lmao.ninja/v2/countries"
    };
  },
  components: {
        BulmaAccordion,
        BulmaAccordionItem
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
