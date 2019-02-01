<template>
  <transition-group name="dot" tag="svg" :width="size" :height="size" appear>
    <dot
      v-for="(dot, index) in dots"
      :key="dot.division + '-' + dot.row + '-' + dot.col"
      :size="size"
      :division="dot.division"
      :col="dot.col"
      :row="dot.row"
      @hover="divide(index)"
    ></dot>
  </transition-group>
</template>

<script>
import dot from "./Dot";

export default {
  data() {
    return {
      size: 800,
      dots: [
        {
          division: 1,
          col: 1,
          row: 1,
          entered: false
        }
      ]
    };
  },
  components: {
    dot
  },
  methods: {
    divide(index) {
      let dot = this.dots[index];
      if (dot.division < 32) {
        for (var m of Array(2).keys()) {
          for (var n of Array(2).keys()) {
            this.dots.push({
              division: dot.division * 2,
              col: dot.col * 2 - m,
              row: dot.row * 2 - n
            });
          }
        }
        this.dots.splice(index, 1);
      }
    }
  }
};
</script>

<style type="text/css">
.dot-enter-active {
  transition: all 0.5s;
}
.dot-enter {
  opacity: 0;
}
</style>
