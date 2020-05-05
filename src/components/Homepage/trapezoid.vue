<template>
  <div>{{content}}</div>
</template>

<script>
export default {
  name: 'trapezoid',
  data() {
    return {
      content: 'NULL',
    };
  },
  methods: {
    changeContent(newContent) {
      this.content = newContent;
    },
  },
};
</script>

<style>

</style>
