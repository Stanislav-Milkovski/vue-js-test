<template>
  <a class="card" :href="breweryInfo.website_url">
    <h1></h1>
    <p>Type: {{ breweryInfo.brewery_type }}</p>
    <main :class="{ hidden: !infoActive }">
      
      <p>Name: {{ breweryInfo.name }}</p>
      <p>Phone: {{ breweryInfo.phone }}</p>
      <p>Country: {{ breweryInfo.country }}</p>
      <p>City: {{ breweryInfo.city }}</p>
      <p>State: {{ breweryInfo.state }}</p>
      <p>Street: {{ breweryInfo.street }}</p>
    </main>
    <footer>
      <button @click.stop="infoActive = !infoActive">
        <span>
          Show Info
        </span>
      </button>
    </footer>
  </a>
</template>

<script>
export default {
  name: 'BreweryListItem',
  props: ['breweryInfo','filter'],
  data() {
    return {
      infoActive: false
    }
  },
};
</script>

<style scoped>
.hidden {
  display: none;
}
.card {
  border: 1px solid #f0f0f0;
  border-radius: 6px;
  padding: 12px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  text-decoration: none;
}

h1 {
  font-size: 1.2rem;
}

h1,
p {
  color: rgba(0, 0, 0, 0.87);
}

button {
  width: 100%;
  text-align: center;
  padding: 12px;
  border: 1px solid #f3f3f3;
  cursor: pointer;
  text-transform: uppercase;
  font-weight: bold;
  color: #fff;
  background: #61b049;
}

.active {
  background: red;
}
</style>
