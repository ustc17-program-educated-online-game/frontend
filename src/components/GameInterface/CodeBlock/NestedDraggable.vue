<template>
  <draggable class="dragArea" tag="ul" :list="tasks" :group="{ name: 'people' }">
    <li v-for="el in tasks" :key="el.id">
      <p
        class="list-group-item list-group-item-success codes"
      >
        {{ el.name }}
      </p>
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
}
.codes {
  width: 400px;
}
</style>
