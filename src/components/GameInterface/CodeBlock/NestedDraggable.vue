<template>
  <draggable class="dragArea" tag="ul" :list="tasks" :group="{ name: 'people' }">
    <li v-for="el in tasks" :key="el.id">
      <div class="container">
        <div class="row">
          <p
            :style="el.embeded? embeded : normal"
            class="list-group-item list-group-item-success name"
          >
            {{ el.name }}
          </p>
          <div
            class="list-group-item list-group-item-secondary condition col-8"
            v-if="el.embeded"
          >
            <div class="inspect">
              inspect()
            </div>
            <select id="inputState" class="relation">
              <option selected>==</option>
              <option>!=</option>
            </select>
            <select id="inputState" class="right-value">
              <option selected>Blank</option>
              <option>Obstacle</option>
              <option>Treasure</option>
              <option>Edge</option>
            </select>
          </div>
        </div>
      </div>
      <nested-draggable :tasks="el.tasks" v-if="el.embeded"/>
    </li>
  </draggable>
</template>
<script>
import draggable from 'vuedraggable';

export default {
  props: {
    tasks: {
      required: true,
      type: Array,
    },
  },
  data() {
    return {
      normal: {
        width: '400px',
        padding: '0',
        margin: '0',
        height: '50px',
      },
      embeded: {
        width: '100px',
        padding: '0',
        margin: '0',
      },
    };
  },
  components: {
    draggable,
  },
  name: 'nested-draggable',
};
</script>
<style scoped>
.dragArea {
  min-height: 50px;
  outline: 1px dashed;
  width: 400px;
}
.condition {
  left: 50px;
  height: 55px;
  padding: 0px;
  width: 300px;
}
.inspect {
  position: absolute;
  top: 20%;
  width: 10%;
  left: 5%;
}
.relation {
  position: absolute;
  top: 20%;
  left: 35%;
  width: 20%;
  height: 60%;
}
.right-value {
  position: absolute;
  top: 20%;
  left: 60%;
  width: 30%;
  height: 60%;
}
</style>
