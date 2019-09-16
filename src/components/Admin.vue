<template>
  <div class="admin" id="admin">
    <header id="title-header" class="clearfix">
      <div id="title-left"></div>
      <div id="title-main"></div>
      <div id="title-right">
        <img src="../assets/images/head/user2-160x160.png" alt="">
        <span>{{msg}}</span>
      </div>
    </header>
    <div id="admin-aside">
      <el-radio-group id="aside-top" v-model="isCollapse" style="margin-bottom: 20px;">
        <el-radio-button :label="false"><i class="iconfont icon-caidanzhengfangxing-"></i></el-radio-button>
        <el-radio-button :label="true"><i class="iconfont icon-fangda"></i></el-radio-button>
      </el-radio-group>

      <ul id="aside-left">
        <el-menu default-active="1-4-1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" :collapse="isCollapse">
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span slot="title">导航一</span>
            </template>
            <el-menu-item-group>
              <span slot="title">分组一</span>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="1-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="1-4">
              <span slot="title">选项4</span>
              <el-menu-item index="1-4-1">选项1</el-menu-item>
            </el-submenu>
          </el-submenu>
          <el-menu-item index="2">
            <i class="el-icon-menu"></i>
            <span slot="title">导航二</span>
          </el-menu-item>
          <el-menu-item index="3" disabled>
            <i class="el-icon-document"></i>
            <span slot="title">导航三</span>
          </el-menu-item>
          <el-menu-item index="4">
            <i class="el-icon-setting"></i>
            <span slot="title">导航四</span>
          </el-menu-item>
        </el-menu>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Admin',
  data () {
    return {
      msg: '系统管理员',
      isCollapse: true
    }
  },
   methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
  #title-header {
    width: 100%;
    height: 60px;
    background: url('../assets/images/head-bg.png') no-repeat right,linear-gradient(to bottom,#e5e5ea, #d1d1d6);
    background-size: 600px 60px;

    #title-left {
      width: 240px;
      height: 100%;
      background: #007aff url('../assets/images/logo.png') no-repeat 24px 5px;
      background-size: 160px 48px;
      float: left;
    }

    #title-right {
      width: 140px;
      height: 100%;
      line-height: 100%;
      background-size: 160px 48px;
      float: right;

      img {
        width: 30px;
        height: 30px;
        vertical-align: middle;
      }

      span {
        color: #fff;
        line-height: 60px;
      }
    }
  }
  
  #admin-aside {
    float: left;
    // 修改 element ui 样式 时 scoped 会不能穿透 使用deep 穿透
   /deep/ .el-radio-button__inner {    
      border: 0px;
      // margin-left: -50px;
    }
    ul, li {
      padding: 0px;
      margin: 0px;
      list-style: none;
    }
    .el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
  }
    #aside-top {
          width: 240px;
          height: 40px;
          border-bottom: solid 1px #d1d1d6;
          margin-left: -50px;
          // li {
          //   width: 24px;
          //   height: 24px;
          //   display: inline-block;
          // }

          // li:first-child{
          //   background-color: rgb(255,59,48);
          //   border-radius: 50%;
          //   margin-left: -50px;
          //   margin-top: 8px;
          //   margin-right: 40px;

          //   i {
          //     color: #fff;
          //     line-height: 24px;
          //   }
          // }
          // li:last-child{
          //   background-color: rgb(255, 200, 48);
          //   border-radius: 50%;

          //   i {
          //     color: #fff;
          //     line-height: 24px;
          //   }
          // }
      }
    }
</style>
