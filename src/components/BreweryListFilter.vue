<template>
  <section class="filter">
    <select name="" id="" @change="selectedFilter">
      <option :value="filterItem" :key="filterItem" v-for="filterItem in breweryTypes" >{{ filterItem }}</option>
    </select>
  </section>
</template>

<script>
export default {
  data() {
    return {
      breweryTypes: ['all', 'micro', 'contract', 'brewpub', 'regional'],
      chosenFilter: 'all'
    };
  },
  methods: {
    selectedFilter($event) {
    this.$emit('selectFilter', $event.target.value)
    }
  },
}
</script>

<style scoped>
select {
  padding: 12px;
  font-size: 1rem;
  margin-bottom: 24px;
}
.filter {
  display: flex;
  justify-content: space-around;

}
</style>
