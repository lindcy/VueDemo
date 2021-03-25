<template>
<div>
  <div class="block">
    <el-carousel height="150px">
      <el-carousel-item v-for="item in banner" :key="item">
        <img class="titlecd" :src="item.img"/>
      </el-carousel-item>
    </el-carousel>
  </div>
  <div>
    <el-row v-for="item in posts" :key="item">
  <el-col class="picPath"><div class="grid-content bg-purple"><img class="pathcd" :src="item.cover"/></div></el-col>
  <el-col class="picTitle"><div class="grid-content bg-purple-light contantcd">{{item.title}}</div></el-col>
</el-row>
  </div>
</div>
</template>
<style>
  .el-carousel__item:nth-child(2n) {
     background-color: #99a9bf;
  }
  .el-carousel__item:nth-child(2n+1) {
     background-color: #d3dce6;
  }
   .el-row {
    margin-bottom: 10px;
    &:last-child {
      margin-bottom: 0;
    }
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
.pathcd{
    display: block!important;
    width: 100%!important;
    height: 200px;
  }
  .contantcd{
      height: 200px!important;  
      text-align: left;
      padding:0px 0px 0px 10px;
  }
  .titlecd,.block,.el-carousel__container{
    height: 350px!important;
    width: 100%;
    display: block;
  }
  .picPath{
    width: 300px;
  }
    .picTitle{
    width: calc(100% - 300px);
  }
</style>

<script>
 export default {
  name: "Bannere",
  data() {
   return {
    banner:[],
    posts:[]
    };
  },
  mounted() {
    this.$axios.get('http://192.168.89.72:81/v1/mock/page').then(response => {
          this.info = response.data.data;
          this.banner=this.info.banner;
          this.posts=this.info.posts;
      })
  }
};
</script>
