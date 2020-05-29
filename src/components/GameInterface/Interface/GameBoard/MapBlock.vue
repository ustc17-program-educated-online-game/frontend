<template>
  <div>
    <div class="BackDiv" :style="BlockPosition">
      <div class="Empty" v-if="state == 1" :style="InnerBlock">
        <div v-if="x == end.x && y == end.y">
          Destination
        </div>
        <div v-else-if="x == start.x && y == start.y">
          Start
        </div>
        <div v-else>
          Empty
        </div>
      </div>
      <div class="Obstacle" v-else-if="state == 2" :style="InnerBlock">
        Obstacle
      </div>
      <div class="Treasure" v-else :style="InnerBlock">
        <div v-if="x == end.x && y == end.y">
          Destination
        </div>
        <div v-else-if="x == start.x && y == start.y">
          Start
        </div>
        <div v-else>
          Treasure
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MapBlock',
  props: {
    state: Number,
    length: String,
    width: String,
    x: Number,
    y: Number,
    start: {
      x: String,
      y: String,
    },
    end: {
      x: String,
      y: String,
    },
  },
  data() {
    const valueLeft = `${(this.x / this.width) * 100}%`;
    const valueRight = `${(this.y / this.length) * 100}%`;
    const blockWidth = `${(1 / this.length) * 100}%`;
    const blockHeight = `${(1 / this.width) * 100}%`;
    return {
      BlockPosition: {
        position: 'absolute',
        left: valueRight,
        top: valueLeft,
        width: blockWidth,
        height: blockHeight,
        padding: '15px',
        'padding-color': 'red',
      },
      InnerBlock: {
        width: '100%',
        height: '100px',
        padding: '30px',
        'padding-color': 'red',
      },
    };
  },
};
</script>

<style>
.BackDiv {
  background-color: rgb(216, 81, 81);
  padding: 10px;
}
.Empty {
  background-color: rgb(124, 216, 185);
}
.Obstacle {
  background-color: rgb(99, 74, 21);
}
.Treasure {
  background-color: rgb(255, 215, 83);
}
.Destination {
  background-color: rgb(80, 214, 39);
}
</style>
