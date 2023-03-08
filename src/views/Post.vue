<template>
  <div class="main">
    <div class="left" @click="overLay">1</div>
    <div class="right">
      <div class="top" @click="overLay">1</div>
      <div class="bottom">
        <div class="bottom-left" @click="overLay">1</div>
        <div class="bottom-right" @click="overLay">1</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Post",
  data() {
    return {};
  },
  components: {},
  methods: {
    overLay() {
      this.$emit('changeShow')
    },
  },
  mounted() {},
};
</script>

<style scoped>
.main {
  width: 60vw;
  height: 30vw;
  background-color: #eeeeee;
  border-radius: 20px;
  margin-bottom: 20px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  text-align: center;
  vertical-align: middle;
}
.left {
  width: 45%;
  height: 85%;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 2px 2px 4px 1px rgba(0, 0, 0, 0.1);
  line-height: calc(30vw * 0.85);
}
.right {
  width: 45%;
  height: 85%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: stretch;
}
.top {
  width: 100%;
  height: 46%;
  line-height: calc(30vw * 0.85 * 0.46);
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 2px 2px 4px 1px rgba(0, 0, 0, 0.1);
}
.bottom {
  width: 100%;
  height: 46%;
  display: flex;
  justify-content: space-between;
}
.bottom-left,
.bottom-right {
  height: 100%;
  width: 46%;
  line-height: calc(30vw * 0.85 * 0.46);
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 2px 2px 4px 1px rgba(0, 0, 0, 0.1);
}
</style>
