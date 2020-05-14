<template>
  <!-- <div class="GameInterface"> -->
  <code-start></code-start>
  <!-- </div> -->
</template>

<script>
import CodeStart from '../components/GameInterface/CodeBlock/CodeStart.vue';

export default {
  name: 'GameInterface',
  components: {
    CodeStart,
  },
};
</script>

<style>
.GameInterface {
  position: absolute;
  top: 100%;
  left: 0%;
  background-color: bisque;
  width: 100%;
  height: 100%;
}
</style>
