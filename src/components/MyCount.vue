<template>
  <div class="my-counter">
    <button
      :disabled="obj.goods_count === 1"
      @click="obj.goods_count > 1 && obj.goods_count--"
      type="button"
      class="btn btn-light"
    >
      -
    </button>
    <input type="number" class="form-control inp" v-model="obj.goods_count" />
    <button @click="obj.goods_count++" type="button" class="btn btn-light">
      +
    </button>
  </div>
</template>

<script>
export default {
  props: {
    obj: {
      type: Object,
    },
  },
  watch:{
      obj:{
          deep:true,
          handler(){
              if(this.obj.goods_count<1){
                  this.obj.goods_count = 1
              }
          }
      }
  }
};
</script>

<style lang="less" scoped>
.my-counter {
  display: flex;
  .inp {
    width: 45px;
    text-align: center;
    margin: 0 10px;
  }
  .btn,
  .inp {
    transform: scale(0.9);
  }
}
</style>