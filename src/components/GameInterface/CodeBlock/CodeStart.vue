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
          <nested-draggable :tasks="list" />
        </div>
      </div>
    </vue-custom-scrollbar>

    <button type="button" class="btn btn-primary btn-start">Start</button>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
import vueCustomScrollbar from 'vue-custom-scrollbar';
import nestedDraggable from './NestedDraggable.vue';

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
      settings: {
        maxScrollbarLength: 160,
      },
      list1: [
        {
          id: 1,
          name: 'if',
          tasks: [],
          embeded: true,
        },
        {
          id: 2,
          name: 'loop',
          tasks: [],
          embeded: true,
        },
        {
          id: 3,
          name: 'go',
          tasks: [],
          embeded: false,
        },
        {
          id: 4,
          name: 'task 4',
          tasks: [],
          embeded: false,
        },
        {
          id: 5,
          name: 'task 5',
          tasks: [],
          embeded: false,
        },
        {
          id: 6,
          name: 'task 5',
          tasks: [],
          embeded: false,
        },
        {
          id: 7,
          name: 'task 5',
          tasks: [],
          embeded: false,
        },
      ],
      list: [],
    };
  },
  methods: {
    log(evt) {
      window.console.log(evt);
    },
    cloneCode({ name, embeded }) {
      idGlobal += 1;
      return {
        id: idGlobal,
        name,
        tasks: [],
        embeded,
      };
    },
  },
};
</script>
<style>
.PlayerCode {
  width: 100%;
}
.CodeArea {
  width: 200%;
  height: 100%;
}
.CodeBlock {
  position: absolute;
  top: 0%;
  left: 60%;
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
  width: 84%;
  height: 100%;
  background-color: rgb(87, 180, 187);
}
</style>
