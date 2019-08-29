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
      <ul id="aside-top" >
        <li>
          <i class="iconfont icon-caidanzhengfangxing-"></i>
        </li>
         <li>
          <i class="iconfont icon-fangda"></i>
        </li>
      </ul>
      <ul id="aside-left"></ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Admin',
  data () {
    return {
      msg: '系统管理员'
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
    ul, li {
      padding: 0px;
      margin: 0px;
      list-style: none;
    }
    #aside-top {
          width: 240px;
          height: 40px;
          border-bottom: solid 1px #d1d1d6;
          
          li {
            width: 24px;
            height: 24px;
            display: inline-block;
          }

          li:first-child{
            background-color: rgb(255,59,48);
            border-radius: 50%;

            i {
              color: #fff;
              line-height: 24px;
            }
          }
          li:last-child{
            background-color: rgb(255, 200, 48);
            border-radius: 50%;

            i {
              color: #fff;
              line-height: 24px;
            }
          }
      }
    }
</style>
