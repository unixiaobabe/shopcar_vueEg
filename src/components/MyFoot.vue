<template>
  <div class="my-footer">
    <div class="custom-control custom-checkbox">
      <input
        type="checkbox"
        class="form-check-input"
        v-model="isAll"
        id="footercheckbox"
      />
      <label for="footercheckbox" class="custon-control-label"> 全选 </label>
    </div>

    <div>
      <span>合计</span>
      <span class="price">¥{{ allPrice }}</span>
    </div>

    <button type="button" class="footer-btn btn btn-primary">
      结算({{ allCount }})
    </button>
  </div>
</template>

<script>
export default {
  computed: {
    isAll: {
      set(val) {
        //同步到每一个小选框
        this.$emit("changeAll", val);
      },
      get() {
        return this.list.every((item) => item.goods_state === true);
      },
    },
    allCount() {
      //总数量
      return this.list.reduce((prev, next) => {
        if (next.goods_state === true) {
          prev += next.goods_count;
        }
        return prev;
      }, 0);
    },
    allPrice() {
      return this.list.reduce((prev, next) => {
        if (next.goods_state === true) {
          prev += next.goods_count * next.goods_price;
        }
        return prev;
      }, 0);
    },
  },
  props: {
    list: {
      type: Array,
    },
  },
};
</script>

<style lang="less" scoped>
.my-footer {
  position: fixed;
  z-index: 2;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 10px;
  background-color: #fff;
  .price {
    color: red;
    font-weight: bold;
    font-size: 14px;
  }
  .footer-btn {
    min-width: 80px;
    height: 30px;
    line-height: 30px;
    border-radius: 25px;
    padding: 0;
  }
}
</style>