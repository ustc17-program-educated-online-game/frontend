<template>
  <div class="GameInterface">
    <game-board></game-board>
    <check-point-info></check-point-info>
    <game-tools></game-tools>
    <code-start></code-start>
  </div>
</template>

<script>
import GameBoard from '../components/GameInterface/Interface/GameBoard.vue';
import CheckPointInfo from '../components/GameInterface/Interface/CheckPointInfo.vue';
import GameTools from '../components/GameInterface/Interface/GameTools.vue';
import CodeStart from '../components/GameInterface/CodeBlock/CodeStart.vue';

export default {
  name: 'GameInterface',
  components: {
    CodeStart,
    GameBoard,
    CheckPointInfo,
    GameTools,
  },
};
</script>

<style>
.GameInterface {
  position: absolute;
  top: 10%;
  left: 0%;
  background-color: rgb(134, 87, 29);
  width: 100%;
  height: 90%;
}
</style>
