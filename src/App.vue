<!-- Dit is de parent component. Het is alleen mogelijk om vanaf hier data mee te geven naar de kleinere components -->
<template>
<div id="app">
  <header>
    <app-title></app-title>
    <!-- Hier word een component gebruikt -->
    <!-- Omdat dit een parent element is kan er data worden meegegeven aan de component -->
    <!-- Hieronder word de data test gebind aan een aangemaakte variabele msg -->
    <app-indicator :msg='test' v-on:changeTest="testing($event)"></app-indicator>
  </header>

  <nav :style="{transform: navToggle()}">
    <div class="nav-wrap">
      <!-- Hier worden de verschillende linnkjes weergeven van routes  -->
      <!-- De routes worden gedecladeerd in de main.js file in de const routes -->
      <router-link class="nav-item" to='/'>Home</router-link>
      <router-link class="nav-item" to='/users'>Users</router-link>
      <router-link class="nav-item" to='/input'>Input</router-link>
    </div>
    <div :style="{background: currentColor}" @click="navControl" class="nav-button">
      <i class="fas fa-sort-up"></i>
    </div>
  </nav>
  <!-- Hier worden de verschillende route component geladen  -->
  <!-- De routes worden gedecladeerd in de main.js file in de const routes -->
  <router-view v-on:sendingColor="colorReceive($event)" v-on:changeOk="testout($event)"></router-view>
</div>
</template>

<script>
// Hieronder worden het vue instance ge-exporteerd naar t template hierboven, zodat de template gebruikt
// kan maken van de data methods etc van de vue instance
export default {
  data() {
    return {
      openNav: false,
      test: JSON.parse(localStorage.getItem("indicator")),
      test2: "De echt test",
      currentColor: "",
    }
  },
  methods: {
    testing: function(event) {
      this.test = event
    },
    testout: function(event) {
      // console.log(event)
      this.test = JSON.parse(localStorage.getItem("indicator"))
      console.log(this.test)
    },
    colorReceive: function(color){
      this.currentColor = color
    },
    navControl: function(){
      this.openNav = (this.openNav == false?
      this.openNav = true : this.openNav = false)
    },
    navToggle: function(){
      return(
        this.openNav == true ?
        "translateX(-200px)" :
        "translateX(0)"
      )
    }

  }
}
</script>

<style>
html {
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: inherit;
}

header {
  height: 300px;
  background: white;
  border-bottom: solid 5px #E72A75;
}

nav {
  transition: all .2s;
  top: 0;
  height: 100%;
  background: white;
  position: fixed;
  z-index: 100;
  transform: translateX(0);
  width: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  box-shadow: 10px 10px 24px -3px rgba(0, 0, 0, 0.32);
}

.nav-wrap {
  width: 150px;
  height: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
}

.nav-item {
  width: 100%;
  border-bottom: black solid 1px;
  text-decoration: none;
  color: black;
}

.nav-button {
  width: 30px;
  height: 150px;
  background: #E72A75;
  position: absolute;
  right: -30px;
  border-radius: 0 40px 40px 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.hide{
  transform: translateX(-200px);
}
i {
  transform: rotate(90deg);
  font-size: 30px;
  color: white;
}

body {
  margin: 0;
  background: #F3F3F3;
}

router-link {
  color: orange;
}
</style>
