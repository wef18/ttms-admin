<template>
  <div class="ttms-main">
    <el-container>
      <!-- 左侧的菜单栏 -->
      <el-aside width="200px">
        <el-menu default-active="2-1" class="ttms-nav" unique-opened>
          <el-menu-item index="1">
            <i class="el-icon-setting"></i>
            <strong slot="title">全局设置</strong>
          </el-menu-item>
          <el-submenu index="2">
            <template slot="title">
              <i class="el-icon-menu"></i>
              <strong>桌台管理</strong>
            </template>
              <el-menu-item index="2-1">所有桌台</el-menu-item>
              <el-menu-item index="2-2">添加桌台</el-menu-item>
              <el-menu-item index="2-3">删除桌台</el-menu-item>
          </el-submenu>
          <el-menu-item index="3">
            <i class="el-icon-message"></i>
            <strong slot="title">菜品类别</strong>
          </el-menu-item>
          <el-submenu index="4">
            <template slot="title">
              <i class="el-icon-tickets"></i>
              <strong>菜品管理</strong>
            </template>
              <el-menu-item index="4-1">所有菜品</el-menu-item>
              <el-menu-item index="4-2">添加菜品</el-menu-item>
              <el-menu-item index="4-3">删除菜品</el-menu-item>
              <el-menu-item index="4-4">修改菜品</el-menu-item>
          </el-submenu>
          <el-menu-item index="5">
            <i class="el-icon-date"></i>
            <strong slot="title">订单列表</strong>
          </el-menu-item>
          <el-menu-item index="6">
            <i class="el-icon-bell"></i>
            <strong slot="title">安全管理</strong>
          </el-menu-item>
        </el-menu>
      </el-aside>
      <el-container>
        <!-- 顶部的信息栏 -->
        <el-header height="60px"  class="ttms-main_header">
          <main-header></main-header>
        </el-header>
        <!-- 主体部分 -->
        <el-main>
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  beforeCreate () {
    //组件创建之前逍遥检查是否已经登录为管理员
    if(!this.$store.state.adminName){
      this.$router.push('/login')
    }
  }
}
</script>

<style  lang="scss">
  @media screen and (max-width: 1000px) {
    .ttms-main_header {
      width: 750px;
    }
  }
</style>
