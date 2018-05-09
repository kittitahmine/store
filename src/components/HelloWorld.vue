<template>
  <div class="container">
    <div class="columns has-text-centerrd">
      <div class="column">
          <img src="../assets/picture.jpg" width="520" height="128">
      </div>
    </div>
    <div class="columns">
      <div class="column is-6 has-text-right">
       <p class="title is-3"> ชื่อสินค้า </p>
       <p class="title is-3"> จำนวนสินค้า </p>
       <p class="title is-3"> ราคาสินค้า </p>
       <p class="title is-3"> รูป </p>
      </div>
      <div class="column is-3 has-text-left">
        <p> <input class="input is-rounded is-info" type="text" v-model="Product.name"> </p> <br>
        <p> <input class="input is-rounded is-info" type="text" v-model="Product.total" min ="0"> </p> <br>
        <p> <input class="input is-rounded is-info" type="text" v-model="Product.price"> </p> <br>
        <p> <input class="input is-rounded is-info" type="text" v-model="Product.img" > </p> <br>
      </div>
      <div class="column is-3"> </div>
    </div>
      <div class="columns">
        <div class="column">
          <button class="button is-success" @click="AddProduct()" type="submit" > ADD </button>
          <button class="button is-danger" type="reset"> Delete </button>
        </div>
      </div>
    </div>
</template>

<script>

import firebase from 'firebase'
var config = {
  apiKey: 'AIzaSyAMXVlHF_XcI25SOxns6Y8RXbM7fed0iOs',
  authDomain: 'movie-23e2b.firebaseapp.com',
  databaseURL: 'https://movie-23e2b.firebaseio.com',
  projectId: 'movie-23e2b',
  storageBucket: 'movie-23e2b.appspot.com',
  messagingSenderId: '84970092337'
}

var firebaseApp = firebase.initializeApp(config)
var db = firebaseApp.database()

export default {
  data () {
    return {
      Product: {
        name: '',
        total: '',
        price: '',
        img: ''
      }
    }
  },
  methods: {
    AddProduct () {
      db.ref('/Product').push(this.Product)
      this.Product.name = ''
      this.Product.total = ''
      this.Product.price = ''
      this.Product.img = ''
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
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
