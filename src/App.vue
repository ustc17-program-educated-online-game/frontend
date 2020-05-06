/* eslint-disable camelcase */
<template>
  <div id="app">
    <div id="nav">
      <!-- The followings are the navigations in the top of our website -->
      <Trapezoid class="navigation" id="homepage"></Trapezoid>
      <LeftTrapezoid class="navigation" id="game"></LeftTrapezoid>
      <RightTrapezoid class="navigation" id="map"></RightTrapezoid>
      <NavigationContent
        class="NaviContent"
        id="homepage"
        ref="NaviContentHomepage"
        content="Homepage"></NavigationContent>
      <NavigationContent
        class="NaviContent"
        id="game"
        ref="NaviContentGameInterface"
        content="GameInterface"></NavigationContent>
      <NavigationContent
        class="NaviContent"
        id="map"
        ref="NaviContentMapEditor"
        content="MapEditor"></NavigationContent>
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
import NavigationContent from './components/Homepage/NavigationContent.vue';

export default {
  name: 'App',
  components: {
    Trapezoid,
    LeftTrapezoid,
    RightTrapezoid,
    NavigationContent,
  },
  created() {
    this.$refs.NaviContentHomepage.SetContent('Homepage');
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

.navigation#game {
  position: absolute;
  left: 0%;
  top: 0%;
  z-index: -2;
}

.navigation#map {
  position: absolute;
  left: 60%;
  top: 0%;
  z-index: -2;
}

.NaviContent {
  position: absolute;
  top: 5%;
}

.NaviContent#homepage {
  left: 44%;
}

.NaviContent#game {
  left: 8%;
}

.NaviContent#map {
  left: 77%;
}
</style>
