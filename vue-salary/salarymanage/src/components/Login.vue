<template>
    <div class="login_container">
        <div class="login_box">
            <div class="picture_box">
                <img src="../assets/logo.png" alt="">
            </div>

            <el-form ref="loginFormRef" :model="loginForm" :rules="loginFormRules" class="login_form" >

                <el-form-item prop="username" >
                    <el-input  v-model="loginForm.username" prefix-icon="el-icon-s-custom"></el-input>
                </el-form-item>

                <el-form-item prop="password">
                    <el-input  v-model="loginForm.password" prefix-icon="el-icon-lock" type="password" ></el-input>
                </el-form-item>

                <el-form-item class="buttons">

                    <el-button type="primary" @click="goHome" class="loginButton"><!--页面跳转至主界面-->
                        登陆
                    </el-button>

                    <el-button type="info" @click="resetLoginForm">重置</el-button>

                </el-form-item>

            </el-form>
        </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      loginForm: {
        username: '',
        password: ''
      },

      loginFormRules: {

        username: [
          { required: true, message: 'input your id', trigger: 'blur' },
          { min: 3, max: 10, message: 'length is not legal', trigger: 'blur' }
        ],

        password: [
          { required: true, message: 'input your password', trigger: 'blur' },
          { min: 6, max: 15, message: 'length is not legal', trigger: 'blur' }
        ]
      }
    }
  },

  methods: {

    resetLoginForm () {
      this.$refs.loginFormRef.resetFields()
    },

    goHome () {
      if (this.loginForm.username === 'root' && this.loginForm.password === '123456') {
        this.$router.push('/home')
      } else {
        window.alert('用户没有权限')
      }
    }

  }

}

</script>

<style lang="less" scoped>
    .login_container{
        background-color: #2b4b6b;
        height: 100%;
    }

    .login_box {
        background-color: white;
        width: 450px;
        height: 300px;
        border-radius: 3px;
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);

    .picture_box {
        height: 130px;
        width: 130px;
        border: 1px solid white;
        border-radius: 50%;
        padding: 10px;
        padding: 10px;
        box-shadow: 0 0 10px #dddddd;
        position :absolute;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: white;
                     img {
                         width: 100%;
                         height: 100%;
                        border-radius: 50%;
                        background-color: bisque;
                        }

                 }
            }

    .login_form{
        position: absolute;
        top: 35%;
        width: 100%;
        padding:  0 20px;
        box-sizing: border-box;
    }

    .buttons{
        display: flex;
        justify-content: flex-end;
    }

</style>
