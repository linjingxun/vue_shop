<template>
  <div class="login">
    <div class="login_form">
      <!-- 头像部分 -->
      <div class="avatar">
        <img src="../assets/logo.png" alt="" />
      </div>
      <!-- 表单 -->
      <el-form
        ref="formRef"
        class="loginForm"
        :model="formModel"
        :rules="formRules"
      >
        <!-- 用户名 -->
        <el-form-item prop="username">
          <el-input
            prefix-icon="iconfont icon-user"
            v-model="formModel.username"
          ></el-input>
        </el-form-item>
        <!-- 密码 -->
        <el-form-item prop="password">
          <el-input
            prefix-icon="iconfont icon-3702mima"
            v-model="formModel.password"
            show-password
          ></el-input>
        </el-form-item>
        <!-- 按钮 -->
        <el-form-item class="btns">
          <el-button type="primary" @click="formLogin">登录</el-button>
          <el-button type="info" @click="formReset">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      /* 登录表单的数据绑定对象 */
      formModel: {
        username: '',
        password: ''
      },
      /* 表单验证 */
      formRules: {
        // 校验用户名
        username: [
          { required: true, message: '请输入用户名称', trigger: 'blur' },
          { min: 3, max: 8, message: '长度在 3 到 8 个字符', trigger: 'blur' }
        ],
        // 校验密码
        password: [
          { required: true, message: '请输入登录密码', trigger: 'blur' },
          { min: 6, max: 16, message: '长度在 6 到 16 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    /* 重置方法 */
    formReset() {
      this.$refs.formRef.resetFields()
    },
    formLogin() {
      this.$refs.formRef.validate(async v => {
        if (!v) return false
        const { data: res } = await this.$http.post('/login', this.formModel)
        if (res.meta.status !== 200) {
          this.$message.error('登录失败')
        } else {
          this.$message.success('登录成功')
          window.sessionStorage.setItem('token', res.data.token)
          this.$router.push('/home')
        }
      })
    }
  }
}
</script>
<style scoped lang="less">
.login {
  height: 100%;
  background-color: #2b4b6b;
  .login_form {
    width: 450px;
    height: 300px;
    border-radius: 4px;
    background-color: #fff;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    .avatar {
      width: 130px;
      height: 130px;
      border: 1px solid #eee;
      border-radius: 50%;
      padding: 10px;
      box-shadow: 0 0 10px #ddd;
      position: absolute;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: #fff;
      img {
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background-color: #eee;
      }
    }
  }
}
.loginForm {
  position: absolute;
  bottom: 0;
  width: 100%;
  padding: 20px;
  box-sizing: border-box;
  .btns {
    display: flex;
    justify-content: flex-end;
  }
}
</style>
