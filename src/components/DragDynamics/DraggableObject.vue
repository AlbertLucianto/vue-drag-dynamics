<template>
  <div :class="[$style.draggable]" :style="positionStyle"
    @mousedown="startDrag" @touchstart="startDrag">
    <slot>Child Object</slot>
  </div>
</template>

<script>
const startX = 100;
const startY = 100;

export default {
  name: 'draggable-object',
  data() {
    return {
      dragging: false,
      lastPosition: { x: startX, y: startY },
      position: { x: startX, y: startY },
      start: { x: 0, y: 0 },
    };
  },
  computed: {
    positionStyle() {
      const { x, y } = this.position;
      return {
        transform: `translate3d(${x}px, ${y}px, 0)`,
      };
    },
  },
  methods: {
    startDrag(e) {
      const evt = e.changedTouches ? e.changedTouches[0] : e;
      this.dragging = true;
      this.start.x = evt.pageX;
      this.start.y = evt.pageY;
      window.addEventListener('mousemove', this.onDrag);
      window.addEventListener('mouseup', this.stopDrag);
    },
    onDrag(e) {
      const evt = e.changedTouches ? e.changedTouches[0] : e;
      if (this.dragging) {
        this.position.x = this.lastPosition.x + (evt.pageX - this.start.x);
        this.position.y = this.lastPosition.y + (evt.pageY - this.start.y);
      }
    },
    stopDrag() {
      if (this.dragging) {
        this.dragging = false;
        this.lastPosition.x = this.position.x;
        this.lastPosition.y = this.position.y;
      }
      window.removeEventListener('mousemove', this.onDrag);
      window.removeEventListener('mouseup', this.stopDrag);
    },
  },
};
</script>

<style lang="scss" module>
@import './styles/colors.scss';

.draggable {
  width: 100px;
  height: 100px;
  background: $warmRed;
  border-radius: 50%;
  position: relative;
  user-select: none;
}
</style>
