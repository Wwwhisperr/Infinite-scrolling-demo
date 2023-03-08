<template>
  <div class="modal">
    <div class="close" @click="close">关闭</div>
    预览
    </div>
</template>

<script>
export default {
  name: 'Modal',
  data() { 
    return {}
  },
  components:{},
  methods:{
    close(){
      this.$emit('closeModal')
    }
  },
  mounted() {},
 }
</script>

<style scoped>
.modal{
  width: 70vw;
  height: 70vw;
  border-radius: 10px;
  box-shadow: 0px 0px 4px 1px rgba(0, 0, 0, 0.1);
  background: #fff;
  text-align: center;
  line-height: 60vw;
  position: absolute; 
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
}
.close{
  width:60px;
  height: 30px;
  line-height: 30px;
}
</style>