<template>
  <div>
    <BreweryListFilter @selectFilter="getFilter"/>

    <section class="breweries">
      <div class="brewery-item" :key="brewery.id" v-for="brewery in breweries">
        <BreweryListItem v-if="brewery.brewery_type == filter || filter == 'all'" :breweryInfo="brewery" :filter="filter"/>
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios'
import BreweryListItem from './BreweryListItem.vue';
import BreweryListFilter from './BreweryListFilter.vue';

export default {
  name: 'BreweryList',
  components: {
    BreweryListItem,
    BreweryListFilter
  },
  data() {
    return {
      breweries: [],
      filter: 'all'
    }
  },
  methods: {
    async getBreweries() {
      await axios.get('https://api.openbrewerydb.org/breweries')
      .then((response) => {
      this.breweries = response.data
      console.log(this.breweries)
      })
      .catch((err) => console.log(err));
    },
    getFilter(filter) {
      this.filter = filter
    }
  },
  mounted() {
    this.getBreweries()
  },
};
</script>

<style scoped>
.breweries {
  display: grid;
  column-gap: 24px;
  row-gap: 24px;
  justify-items: stretch;
  grid-template: repeat(3, 1fr) ;
  grid-template-columns: 1fr 1fr 1fr;
  max-width: 900px;
  margin: 0 auto;
}
</style>