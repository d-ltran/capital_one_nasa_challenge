<template>
<div class="hero is-fullheight is-info is-bold">
  <div class="hero-body">
    <div class="container">
      <div class="search">
        <h1 class="title has-text-centered">Nasa Search</h1>
        <div class="box">
          <h2>Type In Your Search Term</h2>
          <form v-on:submit.prevent="getResult(query,start_date, end_date)">
            <!-- <form v-on:submit.prevent="getResult(query)"> -->
            <input type="text" v-model="query" placeholder="Type in your search" />
            <input type="text" v-model="start_date" placeholder="Enter start year" />
            <input type="text" v-model="end_date" placeholder="Enter end year" />
            <button v-on:click="getResult(query, start_date, end_date)"> Submit</button>
          </form>

          <div class="results" v-if="results">
            <h3> Results</h3>
            <div v-for="result in results">
              <img v-bind:src="result.links[0].href" />
              <button v-on:click="meta()"> View</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>

import axios from 'axios';

export default {
  name: 'search',
  data() {
    return {
      msg: 'Search',
      query: '',
      results: '',
      start_date: '1920',
      end_date: '2019',
      data_array: []
    }
  },

  methods: {
    getResult: function(query, start_date, end_date) {
      // getResult(query) {
      // axios.get('https://images-api.nasa.gov/search?q=' + query + '&year_start=%' + this.start_date + '&year_end=%' + this.end_date + '&media_type=image').then(response => {
      axios.get('https://images-api.nasa.gov/search?q=' + this.query + '&media_type=image&year_start=' + this.start_date + '&year_end=' + this.end_date).then(response => {
        console.log(response.data.collection.items, start_date, end_date);
        this.results = response.data.collection.items;
        this.data_array = response.data.collection.items.data[0];
      });
    },
    meta: function() {
      alert("I attempted to fetch metadata however, my code was not functioning. So I decided to instead display a short message instead of having a broken interface.");
    }
  }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.results img {
  height: 300px;
  margin: 10px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
