/* eslint-disable camelcase */
<template>
  <div id="app">
    <div id="nav">
      <!-- The followings are the navigations in the top of our website -->
      <Trapezoid class="navigation" id="homepage"></Trapezoid>
      <LeftTrapezoid class="navigation" id="leftside"></LeftTrapezoid>
      <RightTrapezoid class="navigation" id="rightside"></RightTrapezoid>
      <router-link to="/">Home</router-link> |
      <router-link to="/GameInterface">GameInterface</router-link> |
      <router-link to="/MapEditor">MapEditor</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
import Trapezoid from './components/Homepage/Trapezoid.vue';
import LeftTrapezoid from './components/Homepage/LeftTrapezoid.vue';
import RightTrapezoid from './components/Homepage/RightTrapezoid.vue';

export default {
  name: 'App',
  components: {
    Trapezoid,
    LeftTrapezoid,
    RightTrapezoid,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  top: 0%;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.navigation#homepage {
  position: absolute;
  left: 30%;
  top: 0%;
  z-index: -1;
}

.navigation#leftside {
  position: absolute;
  left: 0%;
  top: 0%;
  z-index: -2;
}

.navigation#rightside {
  position: absolute;
  left: 60%;
  top: 0%;
  z-index: -2;
}
</style>
