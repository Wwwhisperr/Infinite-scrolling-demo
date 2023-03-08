<template>
  <div class="main-page" @scroll="getDataData">
    <post v-for="i in showData" @changeShow="changeShow"></post>
    <modal v-if="isShow" @closeModal="closeModal"/>
  </div>
</template>

<script>
import Post from "@/views/Post.vue";
import Modal from '@/views/Modal.vue';
export default {
  name: "MainPage",
  data() {
    return {
      // 页数
      pageNum: 0,
      // 每页几个
      pageSize: 6,
      // 模拟数据数组
      allData: [1,2,3,4,5,6,7,8,9,1,2,3,4,5,6,7,8,9,1,2,3,4,5,6,7,8,9],
      // 显示的数据
      showData: [],
      // 是否加载中
      loading: false,
      // 所有数据是否读完
      isEnd: false,
      // modal显示
      isShow:false
    };
  },
  components: {
    Post,
    Modal
  },

  created() {
    this.showData = this.allData.slice(0, this.pageSize);
  },
  methods: {
    getDataData(event) {
      //vue中获取滚动条到底部的距离
      let scrollBottom =
        event.target.scrollHeight -
        event.target.scrollTop -
        event.target.clientHeight;
      //以下三个条件不执行数据加载：1.数据正在加载的状态，2.已经到底了，3.滚动条距离底部的距离小于100px
      if (!this.loading && !this.isEnd && scrollBottom < 50) {
        this.loadData();
      }
    },

    loadData() {
      this.loading = true;
      console.log('加载中...');
      this.getData(this.allData).then(res=>{
        this.showData = res
        this.loading=false
      }).catch(res=>{
        this.isEnd=res
        console.log('到底了');
      })

      console.log(this.showData);
      console.log('加载完毕...');
    },
    // 异步拉取
    getData() {
      return new Promise((resolve, reject) => {
        if (!this.isEnd) {
          this.pageNum += 1;
          let showData=this.allData.slice(0, this.pageNum * this.pageSize);
          if (this.showData.length == this.allData.length) {
            let isEnd = true;
            reject(isEnd)   
          }
          resolve(showData)
        }
      });
    },
    changeShow(){
      this.isShow=!this.isShow
    },
    closeModal(){
      this.isShow=false
    }
  },
};
</script>

<style scoped>
.main-page {
  max-height: 100vh;
  min-height: 100vh;
  overflow: scroll;
}

/* ::-webkit-scrollbar {
        width: 0px;
    }  */
</style>
