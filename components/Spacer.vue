<template>
  <div :style="style"></div>
</template>

<script>
export default {
  name: "Spacer",
  props: ["width"],
  computed: {
    style() {
      return "background: #ccc; height: 1px; width: " + this.width;
    }
  }
};
</script>
