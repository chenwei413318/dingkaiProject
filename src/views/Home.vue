<template>
<el-container class="wrap">
  <el-header height="50px">
    <el-button icon="el-icon-s-unfold" @click="handleOpen"/>
    <the-header />
  </el-header>
  <el-container class="body-wrap">
    <the-nav :class="{'open': open}" />
    <el-main>
      <div class="main">
        <router-view></router-view>
      </div>
    </el-main>
  </el-container>
</el-container>
</template>
<script>
import TheHeader from '@/components/TheHeader'
import TheNav from '@/components/TheNav'
import CarouselTable from '@/views/CarouselTable'
export default {
  name: 'home',
  data () {
    return {
      open: false
    }
  },
  components: {
    TheHeader,
    TheNav,
    CarouselTable
  },
  methods: {
    handleOpen () {
      this.open = !this.open
      console.log(this.open)
    }
  }
}
</script>
<style scoped lang="scss">
@import '~@/common/css/base.scss';
.wrap {
  min-height: 96vh;
  .el-header {
    position: relative;
    background-color: white;
    line-height: 40px;
    .el-button {
      position: absolute;
      left: 10px;
      top: 50%;
       font-size: 20px;
      transform: translateY(-60%);
      border: #fff;
      background-color: #fff;
      @media screen and (min-width: $smallSize){
        display: none
      }
    }
  }
  .body-wrap {
    position: relative;
    overflow: hidden;
    .el-aside {
      z-index: 999;
      min-width: 200px;
      max-width: 200px;
      height: calc(100vh - 100px);
      background-color: rgb(246, 248, 250);
      color: #333;
      @include tran-horizontal(0, 0.4s);
      @media screen and (max-width: $smallSize) {
        position: absolute;
        left: -200px;
      };
      &.open {
        @include tran-horizontal(100%, 0.4s);
      }
    }
    .el-main {
      z-index: 1;
      background-color: rgb(228, 225, 225);
      color: #333;
      text-align: center;
      padding: 10px;
      .main {
        background-color: #fff;
        padding: 10px;
        border-radius: 10px;
        min-height: calc(100vh - 200px)
      }
    }
    .el-footer {
      color: #333;
      line-height: 70px;
      text-align: center;
      background-color: #D3DCE6;
    }
  }
}
</style>
