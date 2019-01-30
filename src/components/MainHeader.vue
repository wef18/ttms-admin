<template>
  <div class="ttms-mainheader">
    <h3>天天美食管理后台</h3>
    <div>
      <span>登录用户：</span>
      <span>{{this.$store.state.adminName}}</span>
      <el-button class="btn" @click="outLogin">退出</el-button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    outLogin () {
      this.$router.push('/login')
    }
  }
}
</script>

<style lang="scss">
  .ttms-mainheader {
    height: 60px;
    background-color: #f4f4f5;
    color: #909399;
    line-height: 60px;
    padding-right: 20px;
    border-radius: 6px;
    display: flex;
    justify-content: space-between;
    h3 {
      margin: 0 20px;
      font-weight: 400;
    }
    div {
      span:nth-child(2) {
        padding-right: 10px;
      }
      .btn {
        padding: 7px 15px;
      }
    }
  }
</style>