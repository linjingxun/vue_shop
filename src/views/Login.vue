<template>
  <div class="login">
  <div style="background-color:#ffffff; width:450px;height:300px">
    <el-input v-model="input" placeholder="请输入内容"></el-input>
    <el-input placeholder="请输入密码" v-model="input" show-password></el-input>
    <el-button type="primary">登录</el-button>
    <el-button type="info">重置</el-button>
  </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      input: ''
    }
  }
}
</script>
<style>

</style>
