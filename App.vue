<template>
  <div id="app container is-fluid">
    <div class="tile is-ancestor">
      <div class="tile is-parent">
        <article class="tile is-child box">
          <p class="subtitle centered">Case Distribution</p>
          <CaseDistributionPie/>
    
    </article>
  </div>
  
  <div class="tile is-ancestor">
  <div class="tile is-parent">
    <article class="tile is-child box">
      <p class="subtitle centered">{{ updateCountryLabel(activeCasesCountry, 'Active Cases')}}</p>

        <ActiveCasesLineChart :country="activeCasesCountry.value"/>

        <div class="columns margin-top-1">
          <div class="column"></div>
          <div class="column">
            <DropDown v-on:country-changed="(country) => activeCasesCountry = country" />
          </div>
          <div class="column"></div>
        </div>
    </article>
    </div>
  </div>
    </div>
  </div>
  
</template>

<script>
import CaseDistributionPie from './components/CaseDistributionPie.vue'
import ActiveCasesLineChart from './components/ActiveCasesLineChart.vue'
import DropDown from './components/DropDown.vue'

export default {
  name: 'App',
  components: {
    CaseDistributionPie,
    ActiveCasesLineChart,
    DropDown
    
  },
  data: () => ({
    activeCasesCountry: ''
  }),
  methods: {
    updateCountryLabel: function (country, defaultText) {
      if(country && country.displayText) {
        return `${defaultText} - ${country.displayText}`;
        }
        return defaultText;
    }
  }
}
</script>

<style>
@import "../node_modules/bulma/css/bulma.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
