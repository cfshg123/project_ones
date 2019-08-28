
<template>
  <!--
  el-form : 表单
   - model : 表单数据对象
   - rules : 验证规则 (待会)
   - ref : 获取组件
   - label-width 标签宽度
     - 如果设置一个具体的值 : 在文本框的左边
     - 如果不设置值,默认占一行

  el-form-item 表单元素
     - label : 标签内容
     - prop : 用来校验,重置的

  span='8'
  :span='8'
  -->
  <el-row
    type='flex'
    justify='center'
    align='middle'
  >
    <el-col :span='8'>
      <el-form
        :model="loginForm"
        :rules="rules"
        ref="loginForm"
      >
        <el-form-item
          label="用户名"
          prop="username"
        >
          <el-input v-model="loginForm.username"></el-input>
        </el-form-item>
        <el-form-item
          label="密码"
          prop="password"
        >
          <el-input v-model="loginForm.password"></el-input>
        </el-form-item>
        <!-- 登录和重置 -->
        <el-form-item>
          <el-button
            type='success'
            @click='startLogin'
          >登录</el-button>
          <el-button @click='resetForm'>重置</el-button>
        </el-form-item>
        <!-- <h1>我是login里的 h1 </h1> -->
      </el-form>

    </el-col>
  </el-row>
</template>

<script>
/* eslint-disable */
// import axios from 'axios'
export default {
  data () {
    return {
      loginForm: {
        username: 'admin',
        password: '123456'
      },
      rules: {
        // 校验用户名
        username: [
          /**
           * 判断 填不填
           * required: true 必填 (*)
           * message : 提示信息
           * trigger: 'blur' 失去焦点的时候触发
           */
          { required: true, message: '请输入用户名', trigger: 'blur' },
          // 判断 格式
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
        ],
        // 校验密码
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          // 判断 格式
          { min: 5, max: 10, message: '长度在 5 到 10 个字符', trigger: 'blur' }
        ]
      }
    };
  },
  methods: {
    //登录
    startLogin () {

      // 校验
      // valid 布尔 (true/false)
      // async function (valid){}
      this.$refs.loginForm.validate(async (valid) => {

        //异常截流
        if (!valid) {
          return false
        }

        // 登录
        let res = await this.$axios.post('http://localhost:8888/api/private/v1/login', this.loginForm)

        if (res.data.meta.status === 200) {

          // 0. 把 token 保存到本地
          localStorage.setItem('token', res.data.data.token)

          // 1. 提示成功
          this.$message({
            message: '登录成功',
            type: 'success',
            duration: 800
          })
          //2. 跳转 home 页
          this.$router.push('/home')

        } else {
          // console.log('登录失败');
          this.$message({
            message: '登录失败',
            type: 'error',
            duration: 800
          })
        }

        // console.log('可以正常登录了');
        // axios.post(url,data,config)
        // this.$axios.post('http://localhost:8888/api/private/v1/login', this.loginForm).then(res => {
        //   console.log(res);
        // if (res.data.meta.status === 200) {

        //   // 0. 把 token 保存到本地
        //   localStorage.setItem('token', res.data.data.token)

        //   // 1. 提示成功
        //   this.$message({
        //     message: '登录成功',
        //     type: 'success',
        //     duration: 800
        //   })
        //   //2. 跳转 home 页
        //   this.$router.push('/home')

        // } else {
        //   // console.log('登录失败');
        //   this.$message({
        //     message: '登录失败',
        //     type: 'error',
        //     duration: 800
        //   })
        // }

        // })

      })
    },
    // 重置
    // 把数据恢复到默认值
    resetForm () {
      this.$refs.loginForm.resetFields();
    }
  }
}
</script>
<style scoped>
.el-row {
  height: 100%;
  background: #2d434c;
}

.el-form {
  background: #fff;
  padding: 20px 30px;
  border-radius: 20px;
}

h1 {
  color: red;
}
</style>
