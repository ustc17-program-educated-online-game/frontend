<template>
  <div class="GameBoard">
    <div v-for="(states, index1) in DataSet.map.state" :key="index1">
      <div v-for="(state, index2) in states" :key="index2">
        <map-block
          :state=state
          :length=DataSet.map.length
          :width=DataSet.map.width
          :x=index1
          :y=index2
          :start=DataSet.map.start
          :end=DataSet.map.end
          >
        </map-block>
      </div>
    </div>
    <character
      :type=DataSet.map.character.type
      :length=DataSet.map.length
      :width=DataSet.map.width
      :x=DataSet.map.character.x
      :y=DataSet.map.character.y
      :state=DataSet.map.character.state
      ></character>
  </div>
</template>

<script>
import TestJson from './test.json';
import MapBlock from './GameBoard/MapBlock.vue';
import Character from './GameBoard/Character.vue';

export default {
  name: 'GameBoard',
  data() {
    return {
      test: 10,
      DataSet: {
        state: String,
        message: String,
        map: {
          id: Number,
          name: String,
          length: Number,
          width: Number,
          state: null,
          start: {
            x: Number,
            y: Number,
          },
          end: {
            x: Number,
            y: Number,
          },
          treasure: {
            x: Number,
            y: Number,
            collected: Boolean,
          },
          character: {
            type: Number,
            x: Number,
            y: Number,
            state: String,
          },
        },
        actionList: null,
      },
    };
  },
  created() {
    this.DataSet = TestJson;
  },
  components: {
    MapBlock,
    Character,
  },
  methods: {
    getMap(mapid) {
      const ThisComponent = this;
      const MapDatabaseQueryPath = '';
      ThisComponent.$http.get(MapDatabaseQueryPath + mapid).then((response) => {
        ThisComponent.DataSet = JSON.parse(response.body);
      });
    },
    setMap(mapid) {
      this.map = {
        id: mapid,
      };
    },
  },
};
</script>

<style>
.GameBoard {
  position: absolute;
  top: 0%;
  left: 0%;
  width: 60%;
  height: 80%;
  background-color: #fff;
}
</style>
