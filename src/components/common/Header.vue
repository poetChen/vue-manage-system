<template>
  <div class="header">
    <div class="collapse-btn" @click="collapseChange">
      <i v-if="!collapse" class="el-icon-s-fold"></i>
      <i v-else class="el-icon-s-unfold"></i>
    </div>
    <div class="logo">后台管理系统</div>
    <div class="header-right">
      <div class="header-user-con">
        <!-- 全屏 -->
        <div class="btn-fullscreen">
          <el-tooltip effect="dark" :content="fullscreen?'取消全屏':'全屏'" placement="bottom">
            <i class="el-icon-rank"></i>
          </el-tooltip>
        </div>
        <!-- 消息中心 -->
        <div class="btn-bell">
          <el-tooltip effect="dark" :content="message?'有${message}条未读消息':'消息中心'" placement="bottom">
            <i class="el-icon-bell"></i>
          </el-tooltip>
          <span class="btn-bell-badge" v-if="message"></span>
        </div>
        <!-- 头像 -->
        <div class="user-avator">
          <img src="../../assets/img/img.jpg" alt="">
        </div>
        <!-- 用户下拉菜单 -->
        <el-dropdown class="user-name">
          <span class="el-dropdown-link">
            {{username}}
            <i class="el-icon-caret-bottom"></i>
          </span>
            <el-dropdown-menu  slot="dropdown">
              <el-dropdown-item>项目仓库</el-dropdown-item>
              <el-dropdown-item>退出登录</el-dropdown-item>
            </el-dropdown-menu>
        </el-dropdown>
      </div>
    </div>
  </div>
</template>

<script>
  import bus from '../common/bus'
  export default  {
      data() {
        return {
          collapse: false,
          fullScreen: false,
          message: 2
        }
      },
      computed: {
        username() {
          let username = localStorage.getItem('ms_username')
          return username ? username : this.name;
        }
      },
      methods: {
        // 侧边栏折叠
        collapseChange() {

        }
      }
  }
</script>

<style scoped>
  .header {
    width: 100%;
    height: 70px;
    background-color: #242f42;
  }
  .collapse-btn {
    color: #FFFFFF;
    float: left;
    font-size: 24px;
    padding: 0 21px;
    line-height: 70px;
  }
  .logo {
    width: 250px;
    line-height: 70px;
    color: #FFFFFF;
    font-size: 25px;
    float: left;
  }
  .header-right {
    color: #FFFFFF;
    float: right;
    padding-right: 50px;
  }
  .header-user-con {
    display: flex;
    height: 70px;
    align-items: center;
  }
  .btn-fullscreen {
   transform: rotate(45deg);
   font-size: 24px;
   margin-right: 5px;
  }
  .user-avator {
    margin-left: 20px;
  }
  .user-avator img {
    width: 40px;
    height: 40px;
    border-radius: 50%;
  }
  .btn-bell,
  .btn-fullscreen {
    width: 30px;
    height: 30px;
    cursor: pointer;
    position: relative;
    text-align: center;
    border-radius: 15px;
  }
  .btn-bell {
    font-size: 22px;
  }
  .btn-bell-badge {
       position: absolute;
       right: 0;
       top: -2px;
       width: 8px;
       height: 8px;
       border-radius: 4px;
       background: #f56c6c;
       color: #fff;
  }
  .user-name {
    margin-left: 10px;
  }
  .el-dropdown-link {
      color: #fff;
      cursor: pointer;
  }
</style>
