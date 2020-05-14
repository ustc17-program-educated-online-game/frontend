<template>
  <div :id="id" class="CodeZone" @dragover.prevent @drop.prevent="drop"><slot/></div>
</template>

<script>
export default {
  props: ['id'],
  methods: {
    drop: (e) => {
      const codeId = e.dataTransfer.getData('codeId');
      const code = document.getElementById(codeId);
      code.style.display = 'block';
      e.target.appendChild(code);
    },
  },
};
</script>

<style>
.CodeZone {
  top: 100%;
  background-color: rgb(54, 78, 214);
  width: 30%;
  height: 50%;
}
</style>
