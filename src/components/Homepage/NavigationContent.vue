<template>
  <div class="content">{{content}}</div>
</template>

<script>
export default {
  name: 'NavigationContent',
  props: ['content'],
};
</script>

<style>
.content {
  font-family: 'Courier New', Courier, monospace;
  font-size: 200%;
}
</style>
