<template>
  <div class="example">
    <drag-board>
      <draggable-object slot="draggable">
        <img :src="imgSource" class="child-draggable" draggable="false"/>
      </draggable-object>
      <draggable-object slot="draggable">
        <img :src="imgSource" class="child-draggable" draggable="false"/>
      </draggable-object>
      <draggable-object slot="draggable">
        <img :src="imgSource" class="child-draggable" draggable="false"/>
      </draggable-object>
      <draggable-object slot="draggable">
        <img :src="imgSource" class="child-draggable" draggable="false"/>
      </draggable-object>
    </drag-board>
  </div>
</template>

<script>
import DraggableObject from './DraggableObject';
import DragBoard from './DragBoard';

export default {
  data() {
    return {
      imgSource: null,
    };
  },
  components: {
    DraggableObject,
    DragBoard,
  },
  mounted() {
    this.$nextTick(() => {
      this.imgSource = 'https://maxcdn.icons8.com/Share/icon/Logos//github_21600.png';
    });
  },
};
</script>

<style lang="scss" scoped>
@import './styles/colors.scss';

.example {
  height: calc(100vh - 20px);
  .child-draggable {
    width: 100px;
    height: 100px;
    margin: auto;
  }
}
</style>
