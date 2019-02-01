<template>
  <circle @mouseover="emit" :cx="cx" :cy="cy" :r="r"></circle>
</template>

<script>
export default {
  name: "Dot",
  props: ["size", "division", "col", "row"],
  computed: {
    cx() {
      return this.size / this.division * this.row - this.r;
    },
    cy() {
      return this.size / this.division * this.col - this.r;
    },
    r() {
      return this.size / this.division / 2;
    }
  },
  methods: {
    emit() {
      this.$emit("hover");
    }
  }
};
</script>
