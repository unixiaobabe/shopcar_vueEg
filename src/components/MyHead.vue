<template>
  <div class="my-head" :style={backgroundColor:background,color}>{{title}}</div>
</template>

<script>
export default {
  props: {
    background: String,
    color: {
      type: String,
      default: "#fff",
    },
    title: {
      type: String,
      require: true,
    },
  },
};
</script>

<style lang="less" scoped>
.my-head {
  height: 45px;
  line-height: 45px;
  text-align: center;
  width: 100%;
  z-index: 2;
}
</style>