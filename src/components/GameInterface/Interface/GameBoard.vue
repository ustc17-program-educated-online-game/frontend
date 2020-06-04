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
      ref="character"
      >
    </character>
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
    takeAction(action) {
      if (action === 'goUp') {
        this.DataSet.map.character.x = String(Number(this.DataSet.map.character.x) - 1);
      } else if (action === 'goDown') {
        this.DataSet.map.character.x = String(Number(this.DataSet.map.character.x) + 1);
      } else if (action === 'goLeft') {
        this.DataSet.map.character.y = String(Number(this.DataSet.map.character.y) - 1);
      } else if (action === 'goRight') {
        this.DataSet.map.character.y = String(Number(this.DataSet.map.character.y) + 1);
      } else if (action === 'turnLeft') {
        if (this.DataSet.map.character.state === 'u') {
          this.DataSet.map.character.state = 'l';
        } else if (this.DataSet.map.character.state === 'r') {
          this.DataSet.map.character.state = 'u';
        } else if (this.DataSet.map.character.state === 'd') {
          this.DataSet.map.character.state = 'r';
        } else if (this.DataSet.map.character.state === 'l') {
          this.DataSet.map.character.state = 'd';
        }
      } else if (action === 'turnRight') {
        if (this.DataSet.map.character.state === 'u') {
          this.DataSet.map.character.state = 'r';
        } else if (this.DataSet.map.character.state === 'r') {
          this.DataSet.map.character.state = 'd';
        } else if (this.DataSet.map.character.state === 'd') {
          this.DataSet.map.character.state = 'l';
        } else if (this.DataSet.map.character.state === 'l') {
          this.DataSet.map.character.state = 'u';
        }
      } else if (action === 'collectSuccess') {
        // eslint-disable-next-line no-console
        console.log('success');
      } else if (action === 'collectFail') {
        // eslint-disable-next-line no-console
        console.log('success');
      }
    },
  },
};
</script>

<style>
.GameBoard {
  position: absolute;
  top: 0%;
  left: 0%;
  width: 85vh;
  height: 85vh;
  background-color: #fff;
}
</style>
