<template>
  <div class="slideDiv">
    <el-carousel :interval="5000" arrow="always" class="lai">
      <el-carousel-item v-for="(item,index) in slideShow" :key="index">
        <div
          class="slideShow"
          :style="`background:url(${$axios.defaults.baseURL+item.url}) center center no-repeat;
        background-size:contain contain`"
        ></div>
      </el-carousel-item>
    </el-carousel>
    <div class="search">
      <el-row>
        <span
          v-for="(item,index) in options"
          :key="index"
          :class="{active:curren==index}"
          @click="handleClick(index)"
        >{{item.name}}</span>
      </el-row>
      <el-row>
        <input type="text" :placeholder="options[curren].search">
        <i class="el-icon-search" ></i>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slideShow: [],
      options: [
        {
          name: "攻略",
          search: "搜索城市"
        },
        {
          name: "酒店",
          search: "请输入酒店名字"
        },
        {
          name: "机票",
          search: "请输入出发地"
        }
      ],
      curren: 0
    };
  },
  mounted() {
    this.$axios({
      url: "scenics/banners",
      mounted: "GET"
    }).then(res => {
      this.slideShow = res.data.data;
    });
  },
  methods: {
    handleClick(index) {
      this.curren = index;
      if(index==2){
        this.$router.push('/air')
      }
    }
  }
};
</script>

<style  lang='less' scoped>
.el-carousel__item h3 {
  color: #475669;
  font-size: 18px;
  opacity: 0.75;
  line-height: 300px;
  margin: 0;
}

.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: #d3dce6;
}
.slideDiv {
  position: relative;
  /deep/ .el-carousel__container {
    height: 700px;

    min-width: 1000px;

    .slideShow {
      width: 100%;
      height: 100%;
      background-color: red;
    }
  }
  .search {
    position: absolute;
    z-index: 999;
    top: 45%;
    left: 38%;
    span {
      width: 82px;
      height: 36px;
      display: inline-block;
      color: #fff;
      background-color: #111;
      line-height: 36px;
      text-align: center; 
    }
    .active {
        background-color: red;
      }
    input {
      background-color: #fff;
      width: 500px;
      height: 50px;
      font-size: 18px;
    }
    i{
      position: absolute;
      right: 12px;
      top: 50%;
      margin-top: -12px;
      font-size: 30px;
    }
  }
}
</style>
