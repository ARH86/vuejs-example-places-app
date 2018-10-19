<template>
  <div class="home">
    <h1>Places App</h1>
  </div>
  <div>
    name: <input v-model="newPlace.name">
    address: <input v-model="newPlace.address">
    <button v-on:click="addPlace()">Add Place</button>
  </div>
</template>

<style>
</style>

<script>
  var axios = require('axios');
export default {
  data: function() {
    return {
      places: [],
      newPlace: {name: " ", address: " "}
    };
  },
  created: function() {
    var params = {
                  name: this.newPlace.name,
                  address: this.newPlace.address
                  };


    axios
    .get("http://localhost:3000/api/places")
    .then(response => {
      this.places = response.data;
    });



  },
  methods: {

    addPlace: function() {
      var params = {
                    name: this.newPlace.name,
                    address: this.newPlace.address
                    };

  axios
  .post("http://localhost:3000/api/places", params)
  .then(response => {
    this.place.push(response.data);
  });   

  this.newPlace = {name: " ", address: " "};               

    };

  },
  computed: {}
};
</script>