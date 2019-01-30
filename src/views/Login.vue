<template>
  <div class="login">
    <el-card class="ttms-login-card">
      <div slot="header">管理员登录</div>
      <div>
        <el-form label-width="100px">
          <el-form-item label="管理员名：">
            <el-input v-model="form.aname" placeholder="请输入管理员名"></el-input>
          </el-form-item>
          <el-form-item label="登录密码：">
            <el-input v-model="form.apwd" type="password" placeholder="请输入管理员密码"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="doLogin">登录</el-button>
            <el-button @click="doCancel">取消</el-button>
          </el-form-item>
        </el-form>
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        aname: 'admin',
        apwd: '123456'
      }
    }
  },
  methods: {
    doLogin () {
      var aname = this.form.aname
      var apwd = this.form.apwd
      var url = this.$store.state.globalSettings.apiUrl+'/admin/login/'+aname+'/'+apwd
      this.$axios.get(url).then((res) => {
        if (res.data.code == 200) {
          //登录成功先把用户名存入Vuex存储仓库中
          this.$store.commit('setAdminName',aname)
          //再跳转到main页面
          this.$router.push('/main')
        } else {
          this.$alert( '用户名或者密码有误', '登录失败', { type: 'error' }).then(()=>{}).catch(()=>{})
        }
      }).catch((err) => {
        console.log(err)
      })
    },
    doCancel () {
      this.form.aname = ''
      this.form.apwd = ''
    }
  }
}
</script>

<style lang="scss">
  .ttms-login-card {
    width: 450px;
    margin: 250px auto;

    .el-card__header {
      text-align: center;
      font-size: 1.2em;
    }
  }
  
</style>