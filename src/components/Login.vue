<template>
    <div id="login" style="width: 100%; height: 100%">
        <div id="login-form">
          <div id="login-left">
            <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" label-width="50px" class="demo-ruleForm" style="margin: 40px">
              <el-form-item label="姓名" prop="username">
                  <el-input v-model.number="ruleForm.username" placeholder="请输入姓名"></el-input>
              </el-form-item>
              <el-form-item label="密码" prop="pass">
                  <el-input type="password" v-model="ruleForm.pass" autocomplete="off" placeholder="请输入密码"></el-input>
              </el-form-item>
              <el-form-item style="margin-top: 50px">
                  <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
                  <el-button @click="resetForm('ruleForm')">重置</el-button>
              </el-form-item>
            </el-form>
          </div>
          <div id="login-right">
          </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
      var checkUserName = (rule, value, callback) => {
        if (!value) {
          return callback(new Error('姓名不能为空'));
        } else {
          callback();
        }
      };
      var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请输入密码'));
        } else {
          callback();
        }
      };
      return {
        ruleForm: {
          username: '',
          pass: '',
        },
        rules: {
          username: [
            { validator: checkUserName, trigger: 'blur' }
          ],
          pass: [
            { validator: validatePass, trigger: 'blur' }
          ],
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            this.$router.replace('/Admin');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>

<style scoped>
  #login {
      width: 100%;
      height: 100%;
      background-image: url('../assets/images/login/login_bg.jpg');
      background-size: 100% 100%;/*按比例缩放*/
      background-repeat: no-repeat;/*还有repeat-x,y等*/
      position: relative;
  }
  #login-form {
    width: 700px;
    height: 400px;
    
    margin: 0 auto;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%)
  }
  #login-form #login-left {
    width: 60%;
    height: 100%;
    background-color: #fff;
    float: left;
    border-radius: 20px 0 0 20px;
  }
   #login-form #login-right {  /* #ffcc00, #ff9500 */
    width: 40%;
    height: 100%;
    background-image: linear-gradient(to bottom , #ffcc00, #ff9500);
    float: right;
    border-radius: 0px 20px 20px 0px;
  }
</style>