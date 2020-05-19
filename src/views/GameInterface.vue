<template>
<<<<<<< HEAD
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
=======
  <!-- <div class="GameInterface"> -->
  <code-start></code-start>
  <!-- </div> -->
</template>

<script>
>>>>>>> c69d58df34e8ecb470158c54bc027a257942bdc1
import CodeStart from '../components/GameInterface/CodeBlock/CodeStart.vue';

export default {
  name: 'GameInterface',
  components: {
    CodeStart,
<<<<<<< HEAD
    GameBoard,
    CheckPointInfo,
    GameTools,
=======
>>>>>>> c69d58df34e8ecb470158c54bc027a257942bdc1
  },
};
</script>

<style>
.GameInterface {
  position: absolute;
<<<<<<< HEAD
  top: 10%;
  left: 0%;
  background-color: rgb(134, 87, 29);
  width: 100%;
  height: 90%;
=======
  top: 100%;
  left: 0%;
  background-color: bisque;
  width: 100%;
  height: 100%;
>>>>>>> c69d58df34e8ecb470158c54bc027a257942bdc1
}
</style>
