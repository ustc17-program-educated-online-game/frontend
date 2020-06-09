/* eslint-disable no-alert */
<template>
  <div class="MapEditor">
    <map-board ref="MapBoard"></map-board>
    <element-board ref="ElementBoard"
    @set-point="SetPoint"
    @select-element="SelectElement"
    @move-element="MoveElement"
    @reset-board="ResetBoard"
    @remove-element="RemoveElement"
    @rotate-character="RotateCharacter">
    </element-board>
    <button type="button" class="btn btn-save btn-secondary"
        >保存</button>
    <button type="button" class="btn btn-test btn-secondary"
        >测试</button>
  </div>

</template>

<script>
import MapBoard from '../components/MapEditor/MapBoard.vue';
import ElementBoard from '../components/MapEditor/ElementBoard.vue';

export default {
  name: 'MapEditor',
  components: {
    MapBoard,
    ElementBoard,
  },
  methods: {
    SetPoint(msg) {
      this.$refs.MapBoard.SetPoint(msg);
    },
    ResetBoard() {
      this.$refs.MapBoard.resetMap();
    },
    SelectElement(msg) {
      this.$refs.MapBoard.SelectElement(msg);
    },
    MoveElement(msg) {
      this.$refs.MapBoard.MoveElement(msg);
    },
    RemoveElement() {
      this.$refs.MapBoard.RemoveElement();
    },
    RotateCharacter() {
      this.$refs.MapBoard.RotateCharacter();
    },
  },
};
</script>

<style>

.MapEditor {
  position: absolute;
  top: 10%;
  left: 0;
  width: 100%;
  height: 90%;
}

.btn-save {
  position: absolute;
  top: 85%;
  left: 68%;
  width: 10%;
  height: 5%;
}

.btn-test {
  position: absolute;
  top: 85%;
  left: 82%;
  width: 10%;
  height: 5%;
}

</style>
