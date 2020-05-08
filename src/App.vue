<template>
  <div id="app">
    <div id="nav">
      <!-- The followings are the navigations in the top of our website -->
      <navigation-background></navigation-background>
      <navigation-bar></navigation-bar>
      <logo></logo>
      <router-link to="/" id="HomepageRouter">Homepage</router-link>
      <router-link to="/GameInterface" id="GameRouter">GameInterface</router-link>
      <router-link to="/MapEditor" id="MapRouter">MapEditor</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
// the followings are importng part of the navigation part
import NavigationBackground from './components/Navigation/NavigationBackground.vue';
import NavigationBar from './components/Navigation/NavigationBar.vue';
import Logo from './components/Navigation/Logo.vue';

export default {
  name: 'App',
  components: {
    NavigationBackground,
    NavigationBar,
    Logo,
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
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: #ee1a72;
}

.navigation#homepage {
  position: absolute;
  left: 30%;
  top: 0%;
  z-index: -9;
}

.navigation#game {
  position: absolute;
  left: 0%;
  top: 0%;
  z-index: -10;
}

.navigation#map {
  position: absolute;
  left: 60%;
  top: 0%;
  z-index: -10;
}

#HomepageRouter {
  font-family: 'Courier New', Courier, monospace;
  font-size: 200%;
  position: absolute;
  top: 5%;
  z-index: 0;
  left: 44%;
}

#GameRouter {
  font-family: 'Courier New', Courier, monospace;
  font-size: 200%;
  position: absolute;
  top: 5%;
  z-index: 0;
  left: 8%;
}

#MapRouter {
  font-family: 'Courier New', Courier, monospace;
  font-size: 200%;
  position: absolute;
  top: 5%;
  z-index: 0;
  left: 77%;
}
</style>
