<template>
  <div class="header">
    <el-row type="flex" justify="space-between" class="el-row">
      <div class="logo">
        <el-row align="middle">
          <nuxt-link to="/">
            <img src="/images/logo.jpg" alt>
          </nuxt-link>
        </el-row>
      </div>
      <div class="navs">
        <nuxt-link to="/">首页</nuxt-link>
        <nuxt-link to="/post">旅游攻略</nuxt-link>
        <nuxt-link to="/hotal">酒店</nuxt-link>
        <nuxt-link to="/air">国内机票</nuxt-link>
      </div>
      <div class="user">
        <el-row>
          <el-dropdown class="personCenter" v-if="true">
            <img src="/images/avatar.jpg" alt>
            <span class="el-dropdown-link">
              爷是个杀猪的
              <i class="el-icon-arrow-down el-icon--right"></i>
            </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>个人中心</el-dropdown-item>
              <el-dropdown-item>退出</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <div class="loginRegister" v-else>
              <nuxt-link to='/login'>登录/注册</nuxt-link>
          </div>
        </el-row>
      </div>
    </el-row>
  </div>
</template>

<script>
export default {
    data(){
        return {
            defaultHover:0
        }
    }
};
</script>
<style lang='less' scoped>
.header {
  width: 1000px;
  margin: 0 auto;
  height: 60px;
  border-bottom: 1px solid #eee;
  box-shadow: 2px 2px 3px #eee;
  .el-row {
    .logo {
      width: 156px;
      height: 43px;
      margin-top: 9px;
      img {
        width: 100%;
      }
    }
    .navs {
      flex: 1;
      height: 100%;
      line-height: 60px;
      a {
        padding: 0 20px;
        &:hover{
            color:red;
            border-bottom:4px solid #409eff;
        }
      }
      .nuxt-link-exact-active{
          background-color: #409eff;
      }
    }
    .user {
      .personCenter {
        display: flex;
        height: 60px;
        align-items: center;
        justify-content: center;
        img {
          width: 36px;
          height: 36px;
        }
        .el-dropdown-link {
          line-height: 60px;
        }
      }
      .loginRegister{
          line-height: 60px;
      }
    }
  }
}
</style>
