<template>
  <div class="search">
    <h1>NASA</h1>
    <h2>{{ msg }}</h2>
    <br>
    <form v-on:submit.prevent="getResult(query)">
      <input type="text" v-model="query" placeholder="search">
    </form>
    <hr>
    <v-container grid-list-md text-xs-center>
      <v-layout row wrap>
        <v-flex class="gallery">
          <v-card class="results px-2" v-for="(result, index) in results" :key="index">
            <img v-bind:src="result.links[0].href">
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "search",
  data() {
    return {
      msg: "Image Search",
      query: "",
      results: ''
    };
  },
  methods: {
    getResult(query) {
      axios
        .get(
          "https://images-api.nasa.gov/search?q=" + query + "#apod_img_id"
        )
        .then(response => {
          this.results = response.data.collection.items;
        });
    }
  }
};
</script>

<style scoped>
h1 {
  font-weight: normal;
  font-size: 4em;
}
h2 {
    font-weight: normal;
    font-size: 1em;
    margin-left:100px;
}
input{
  width: 30%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
.gallery {
  display:flex;
  flex-wrap: wrap;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
img {
    padding: 10px 10px;
    position: relative;
    width: 280px;
    height: 280px;
}
</style>

