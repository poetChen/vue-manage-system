<template>
  <div class="login-wrap">
    <div class="ms-login">
      <div class="ms-title">后台管理系统</div>
      <el-form :model="param" :rules="rules" class="ms-content">
        <el-form-item prop="username">
          <el-input v-model="param.username" placeholder="username">
            <el-button slot="prepend" icon="el-icon-user"></el-button>
          </el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input v-model="param.password" @keyup.enter.native="submitForm()" type="password" placeholder="password">
            <el-button slot="prepend" icon="el-icon-key"></el-button>
          </el-input>
        </el-form-item>
        <div class="login-btn">
          <el-button type="primary" @click="submitForm()">登录</el-button>
        </div>
        <p class="login-tips">Tips:用户名和密码随便填</p>
      </el-form>
    </div>
  </div>
</template>

<script>
  export default {
    data:function(){
      return {
        param: {
          username: 'admin',
          password: '123456',
        },
        rules: {
          username: [{require: true, message: '请输入用户名', trigger: 'blur'}],
          password: [{require: true, message: '请输入密码', trigger: 'blur'}]
        }
      };
    },
    methods:{
      submitForm() {
        this.$router.push('/');
      }
    }
  }
</script>

<style scoped>
  .login-wrap {
    width: 100%;
    height: 100%;
    position: relative;
    background-size: 100%;
    background-image: url(../../assets/img/login-bg.jpg);

  }
  .ms-content {
    padding: 30px 30px;
  }
  .ms-title {
    width: 350px;
    line-height: 45px;
    text-align: center;
    font-size: 20px;
    color: #DDDDDD;
    border-bottom: 1px solid #ddd;
  }
  .ms-login {
    width: 350px;
    position: absolute;
    background-color: rgba(255,255,255,0.3);
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);

  }
  .login-btn button{
    width: 100%;
  }
  .login-tips {
    font-size: 12px;
    color: #fff;
    padding-top: 15px;
  }
</style>
