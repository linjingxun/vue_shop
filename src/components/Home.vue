<template>
  <div class="home">
    <el-form>
      <el-form-item class="btns">
        <el-button type="info" @click="loginOut">退出</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data () {
    return {
    }
  },
  methods: {
    loginOut() {
      window.sessionStorage.clear()
      this.$message('用户登出成功')
      this.$router.push('/login')
    }
  }
}
</script>

<style scoped lang = "less">
</style>
