<template>
  <div class="home">
    <el-container>
      <el-aside width="auto">
        <div class="logo"></div>     
          <el-menu
            :router="true"
            :collapse="isCollapse"
            class="el-menu-admin"
            background-color="#545c64"
            text-color="#fff"
            active-text-color="#ffd04b">
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>用户管理</span>
              </template>
              <el-menu-item index="/user">
                <i class="el-icon-menu"></i>
                <span slot="title">用户列表</span>
              </el-menu-item>
              <el-menu-item index="3">
                <i class="el-icon-menu"></i>
                <span slot="title">导航二</span>
              </el-menu-item>
            </el-submenu>
          </el-menu>
      </el-aside>
      <el-container>
        <el-header class="el-header">
          <i class="myicon myicon-menu toggle-btn" @click="Collapse()"></i>
          <div class="system-title">电商后台管理系统</div>
          <div>
            <span class="welcome">您好{{$store.getters.username}}</span>
                        
            <el-button type="text" @click="loginOut">退出</el-button>
          </div>
        </el-header>
        <el-main>
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>
<script>
export default {
  data(){
    return {
      isCollapse:false
    }
  },
  methods: {
    // handleOpen(key, keyPath) {
    //   console.log(key, keyPath);
    // },
    // handleClose(key, keyPath) {
    //   console.log(key, keyPath);
    // }
    loginOut(){
      this.$message({
          message: '退出成功',
          type: 'success'
        });
      setTimeout(()=>{
        localStorage.removeItem('mytoken')
        localStorage.removeItem('username')
        this.$router.push({name:'login'})
      },1000)
    },
    Collapse(){
      this.isCollapse = !this.isCollapse
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  height: 100%;
  background-color: #E5E5E5;
  .el-menu-admin:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
  }
  .el-container {
    height: 100%;
  }
  .el-aside {
    background-color: #545c64;
  }
  .el-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #009688;
  }
  .logo {
    height:60px;
    background: url(../assets/logo.png);
    background-size: cover;
    background-color: white;
  }
  .toggle-btn {
    padding: 0 10px;
    margin-left: -20px;
    font-size: 36px;
    line-height: 60px;
    color: white;
    cursor: pointer;
    &:hover {
      background-color: #00635a;
    }
  }
  .system-title {
    font-size: 28px;
    color: white;
  }
  .welcome, {
    color: white;
  }
}
</style>
