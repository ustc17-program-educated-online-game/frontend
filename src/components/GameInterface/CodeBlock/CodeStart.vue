<template>
  <div class="row CodeBlock">
    <div class="">
      <draggable
        class="dragArea list-group"
        :list="list1"
        :group="{ name: 'people', pull: 'clone', put: false }"
        tag="ul"
        :clone="cloneCode"
        @change="log"
      >
        <div
          class="list-group-item list-group-item-info"
          v-for="element in list1"
          :key="element.id"
        >
          {{ element.name }}
        </div>
      </draggable>
    </div>

    <vue-custom-scrollbar
      class="scroll-area"
      :settings="settings"
    >
      <div class="row PlayerCode">
        <div class="CodeArea bg-info">
          <nested-draggable :tasks="list" id="codes"/>
        </div>
      </div>
    </vue-custom-scrollbar>

    <button
      type="button"
      class="btn btn-primary btn-start"
      @click="getAllCodes()"
    >
      Start
    </button>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
import vueCustomScrollbar from 'vue-custom-scrollbar';
import nestedDraggable from './NestedDraggable.vue';
import testJSON from '../Interface/test.json';

let idGlobal = 0;

export default {
  name: 'CodeStart',
  components: {
    draggable,
    nestedDraggable,
    vueCustomScrollbar,
  },
  data() {
    return {
      actions: null,
      settings: {
        maxScrollbarLength: 160,
      },
      list1: [
        {
          id: 1,
          name: 'if',
          tasks: [],
          embeded: true,
          extrainfo: false,
        },
        {
          id: 2,
          name: 'while',
          tasks: [],
          embeded: true,
          extrainfo: false,
        },
        {
          id: 3,
          name: 'go',
          tasks: [],
          embeded: false,
          extrainfo: true,
        },
        {
          id: 4,
          name: 'turn left',
          tasks: [],
          embeded: false,
          extrainfo: false,
        },
        {
          id: 5,
          name: 'turn right',
          tasks: [],
          embeded: false,
          extrainfo: false,
        },
        {
          id: 6,
          name: 'open',
          tasks: [],
          embeded: false,
          extrainfo: false,
        },
      ],
      list: [],
    };
  },
  methods: {
    log(evt) {
      window.console.log(evt);
    },
    cloneCode({ name, embeded, extrainfo }) {
      idGlobal += 1;
      return {
        id: idGlobal,
        name,
        tasks: [],
        embeded,
        extrainfo,
      };
    },
    getCodes(object, codeslist) {
      let newcodes = codeslist;
      if (object.className === 'list-group-item list-group-item-success name') {
        if (newcodes !== '') {
          newcodes += ',{';
        } else {
          newcodes = '{';
        }
        if (object.innerText === 'if') {
          newcodes += '"condition":{';
          // add relation to newcodes
          newcodes += '"expression":';
          let relation = object.nextSibling.children[1];
          relation = relation.options[relation.selectedIndex].value;
          newcodes += relation;
          // add relation val to newcodes
          newcodes += ',"val":';
          let val = object.nextSibling.children[2];
          val = val.options[val.selectedIndex].value;
          newcodes += val;
          // add codes part to newcodes
          newcodes += ',"codes":[';
          let codes = object.parentNode.parentNode.nextSibling;
          // eslint-disable-next-line prefer-destructuring
          codes = codes.children[0].children[0].children[0].children[0];
          codes = this.getCodes(codes, '');
          newcodes += codes;
          newcodes += ']}';
          newcodes += '}';
        } else if (object.innerText === 'while') {
          newcodes += '"circulate":{';
          // add relation to newcodes
          newcodes += '"expression":';
          let relation = object.nextSibling.children[1];
          relation = relation.options[relation.selectedIndex].value;
          newcodes += relation;
          // add relation val to newcodes
          newcodes += ',"val":';
          let val = object.nextSibling.children[2];
          val = val.options[val.selectedIndex].value;
          newcodes += val;
          // add codes part to newcodes
          newcodes += ',"codes":[';
          let codes = object.parentNode.parentNode.nextSibling;
          // eslint-disable-next-line prefer-destructuring
          codes = codes.children[0].children[0].children[0].children[0];
          codes = this.getCodes(codes, '');
          newcodes += codes;
          newcodes += ']}';
          newcodes += '}';
        } else if (object.innerText === 'go') {
          newcodes += `"${object.innerText}":"`;
          // eslint-disable-next-line no-console
          newcodes += object.nextSibling.children[0].value;
          newcodes += '"}';
        } else {
          newcodes += `"${object.innerText}":"1"}`;
        }
        let next = object.parentNode.parentNode.parentNode.nextSibling;
        if (next !== null) {
          // eslint-disable-next-line prefer-destructuring
          next = next.children[0].children[0].children[0];
          newcodes = this.getCodes(next, newcodes);
        }
      }
      return newcodes;
    },
    getAllCodes() {
      let FirstSentence = document.getElementById('codes').children[0];
      // eslint-disable-next-line prefer-destructuring
      FirstSentence = FirstSentence.children[0].children[0].children[0];
      let codesstring = this.getCodes(FirstSentence, '');
      codesstring = `{"codes":[${codesstring}]}`;
      // eslint-disable-next-line no-console
      console.log(codesstring);
      const codes = JSON.parse(codesstring);
      // eslint-disable-next-line no-console
      console.log(codes);
      this.getActions();
    },
    getActions() {
      let i = 0;
      const actions = testJSON.actionList;
      const loop = setInterval(() => {
        if (actions[i] !== 'endMissionSuccess' && actions[i] !== 'endMissionFail') {
          while (actions[i] === 'isBlank' || actions[i] === 'isObstacle' || actions[i] === 'isTreasure' || actions[i] === 'isEdge') {
            i += 1;
          }
          this.takeActions(actions[i]);
          i += 1;
        } else {
          clearInterval(loop);
        }
      }, 1000);
      if (actions[i] === 'endMissionSuccess') {
        // eslint-disable-next-line no-console
        console.log('success');
      } else if (actions[i] === 'endMissionFail') {
        // eslint-disable-next-line no-console
        console.log('fail');
      }
    },
    takeActions(action) {
      this.$emit('takeAction', action);
    },
  },
};
</script>
<style>
.PlayerCode {
  width: 500%;
  height: 500%;
}
.CodeArea {
  width: 200%;
  height: 100%;
}
.CodeBlock {
  position: absolute;
  top: 0%;
  left: 70%;
  width: 40%;
  height: 100%;
  margin: 0%;
}
.btn-start {
  position: absolute;
  left: 0%;
  bottom: 0%;
  width: 15.6%;
  height: 10%;
}
.scroll-area {
  width: 80%;
  height: 100%;
  background-color: rgb(87, 180, 187);
}
</style>
