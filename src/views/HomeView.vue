<template>
  <div>
    <my-head title="购物车案例" background="#1d7bff"></my-head>
    <div class="list">
      <my-good v-for="item in list" :key="item.id" :gObj="item"></my-good>
    </div>
    <my-foot @changeAll="allFn" :list="list"></my-foot>
  </div>
</template>

<script>
//@ 指向的是src目录
import MyHead from "@/components/MyHead.vue";
import MyGood from "@/components/MyGood.vue";
import MyCount from "@/components/MyCount.vue";
import MyFoot from "@/components/MyFoot.vue";
export default {
  components: { MyHead, MyGood, MyCount, MyFoot },
  data() {
    return {
      list: [],
    };
  },
  async created() {
    let { data: res } = await this.$http.get("/api/cart");
    this.list = res.list;
  },
  methods: {
    allFn(val) {
      //更改每一个小选框的状态
      this.list.forEach(item => {
        item.goods_state = val;
      });
    },
  },
};
</script>

<style lang="less" scoped>
.list {
  padding-bottom: 50px;
}
</style>