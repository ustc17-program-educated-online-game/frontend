<template>
  <div class="row">
    <div class="col-3">
      <h3>Draggable 1</h3>
      <draggable
        class="dragArea list-group"
        :list="list1"
        :group="{ name: 'people', pull: 'clone', put: false }"
        tag="ul"
        :clone="cloneCode"
        @change="log"
      >
        <div
          class="list-group-item"
          v-for="element in list1"
          :key="element.id"
        >
          {{ element.name }}
        </div>
        <!-- <li v-for="el in list1" :key="el.name">
          <p>{{ el.name }}</p>
          <nested-draggable :tasks="el.tasks" :group="{name: 'people', pull: 'clone', put: false}"/>
        </li> -->
      </draggable>
    </div>

    <div class="row longlong">
      <div class="col-8">
        <h3>Nested draggable</h3>
        <nested-draggable :tasks="list" />
      </div>
    </div>

    <rawDisplayer class="col-3" :value="list1" title="List 1" />

    <rawDisplayer class="col-3" :value="list" title="List" />
  </div>
</template>

<script>
import draggable from 'vuedraggable';
import nestedDraggable from './NestedDraggable.vue';

let idGlobal = 0;

export default {
  name: 'CodeStart',
  components: {
    draggable,
    nestedDraggable,
  },
  data() {
    return {
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
          name: 'task 3',
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
.longlong {
  width: 70%;
}
</style>
