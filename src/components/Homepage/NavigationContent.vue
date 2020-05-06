<template>
  <div class="content"><router-link to=path>{{content}}</router-link></div>
</template>

<script>
export default {
  name: 'NavigationContent',
  props: ['content', 'path'],
};
</script>

<style>
.content {
  font-family: 'Courier New', Courier, monospace;
  font-size: 200%;
}
</style>
