<template>
  <div :class="[$style.board]">
    <slot name="draggable"></slot>
  </div>
</template>

<script>
export default {
  name: 'drag-board',
};
</script>

<style lang="scss" module>
@import './styles/colors.scss';

.board {
  width: 100%;
  height: 100%;
  background: $white;
}
</style>
