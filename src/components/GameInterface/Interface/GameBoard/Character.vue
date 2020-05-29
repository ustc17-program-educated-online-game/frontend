<template>
  <div :style="Character">
    character
  </div>
</template>

<script>
export default {
  name: 'Character',
  props: {
    type: String,
    x: String,
    y: String,
    state: String,
    width: String,
    length: String,
  },
  data() {
    const valueLeft = `${(this.x / this.width) * 100 + 3}%`;
    const valueRight = `${(this.y / this.length) * 100 + 3}%`;
    const blockWidth = `${(1 / this.length) * 80}%`;
    const blockHeight = `${(1 / this.width) * 60}%`;
    // eslint-disable-next-line no-console
    console.log(valueLeft);
    // eslint-disable-next-line no-console
    console.log(valueRight);
    // eslint-disable-next-line no-console
    console.log(blockWidth);
    // eslint-disable-next-line no-console
    console.log(this.width);
    return {
      Character: {
        position: 'absolute',
        left: valueRight,
        top: valueLeft,
        width: blockWidth,
        height: blockHeight,
        padding: '15px',
        'background-color': 'white',
      },
    };
  },
};
</script>

<style>
</style>
