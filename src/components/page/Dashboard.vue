<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="8">
         <el-card shadow="hover" class="mgb20" style="height: 252px;">
           <div class="user-info">
             <img src="../../assets/img/img.jpg" alt="" class="user-avator">
             <div class="user-info-cont">
               <div class="user-info-name">{{name}}</div>
               <div>{{role}}</div>
             </div>
           </div>
           <div class="user-info-list">
             上次登录时间:
             <span>2020-08-28</span>
           </div>
           <div class="user-info-list">
             上次登录地点:
             <span>环球资源</span>
           </div>
         </el-card>
         <el-card shadow="hover" style="height: 252px;">
            <div slot="header" class="clearfix">
              <span>语言详情</span>
            </div>Vue
            <el-progress :percentage="71.3" color="#42b983"></el-progress>JavaScript
            <el-progress :percentage="24.1" color="#f1e05a"></el-progress>CSS
            <el-progress :percentage="13.7"></el-progress>HTML
            <el-progress :percentage="5.9" color="#f56c6c"></el-progress>
         </el-card>
      </el-col>
      <el-col :span="16">
        <el-row :gutter="20" class="mgb20">
          <el-col :span="8">
            <el-card shadow="hover" :body-style="{padding: '0px'}">
              <div class="grid-content grid-con-1">
                <i class="el-icon-user grid-con-icon"></i>
                <div class="grid-cont-right">
                    <div class="grid-num">1234</div>
                    <div>用户访问量</div>
                </div>
              </div>
            </el-card>
          </el-col>
          <el-col :span="8">
            <el-card shadow="hover" :body-style="{padding: '0px'}">
              <div class="grid-content grid-con-2">
                <i class="el-icon-bell grid-con-icon"></i>
                <div class="grid-cont-right">
                    <div class="grid-num">1234</div>
                    <div>用户访问量</div>
                </div>
              </div>
            </el-card>
          </el-col>
          <el-col :span="8">
            <el-card shadow="hover" :body-style="{padding: '0px'}">
              <div class="grid-content grid-con-3">
                <i class="el-icon-s-cooperation grid-con-icon"></i>
                <div class="grid-cont-right">
                    <div class="grid-num">1234</div>
                    <div>用户访问量</div>
                </div>
              </div>
            </el-card>
          </el-col>
        </el-row>
        <el-card shadow="hover" style="height: 403px;">
          <div slot="header" class="clearfix">
            <span>待办事项</span>
            <el-button style="float: right; padding: 3px 0;" type="text">添加</el-button>
          </div>
          <el-table :show-header="false" :data="todoList" style="width: 100%;">
            <el-table-column width="40">
              <template slot-scope="scope">   <!--取到当前单元格-->
                <el-checkbox v-model="scope.row.status"></el-checkbox>    <!--scope.row 直接取到该单元格的值，就是数组里的元素对象，既是todoList[scope.$index]-->
                                                                          <!--.status 是对象里的status属性的值-->
              </template>
            </el-table-column>
            <el-table-column>
              <template slot-scope="scope">
                <div
                  class="todo-item"
                  :class="{'todo-item-del': scope.row.status}"
                >{{scope.row.title}}</div>
              </template>
            </el-table-column>
            <el-table-column width="60">
              <template>
                <i class="el-icon-edit"></i>
                <i class="el-icon-delete"></i>
              </template>
            </el-table-column>
          </el-table>
        </el-card>
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="12">
        <el-card shadow="hover">
          <schart ref="bar" class="schart" canvasId="bar" :options="options"></schart>
        </el-card>
      </el-col>
      <el-col :span="12">
        <el-card shadow="hover">
           <schart ref="line" class="schart" canvasId="line" :options="options2"></schart>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  import Schart from 'vue-schart';
  import bus from '../common/bus';
  export default {
    name: 'dashboard',
    data() {
      return {
        name: localStorage.getItem('ms_username'),
        todoList: [
          {
            title: '今天要写100个bug',
            status: false
          },
          {
            title: '今天要写100个bug',
            status: false
          },
          {
            title: '今天要写100个bug',
            status: false
          },
          {
            title: '今天要写100个bug',
            status: false
          },
          {
            title: '今天要改昨天的100个bug，并增加200个bug',
            status: true
          },
          {
            title: '今天不写bug了，删库跑路吧' ,
            status: true
          }
        ],
        data: [
          {
            name: '2018/09/04',
            value: 1083
          },
          {
            name: '2018/09/05',
            value: 941
          },
          {
            name: '2018/09/06',
            value: 1139
          },
          {
            name: '2018/09/07',
            value: 816
          },
          {
            name: '2018/09/08',
            value: 327
          },
          {
            name: '2018/09/09',
            value: 228
          },
          {
            name: '2018/09/10',
            value: 1065
          }
           ],
        options: {
          type: 'bar',
          title: {
            text: '最近一周各品类销售图'
          },
          xRorate: 25,
          labels: ['周一','周二','周三','周四','周五'],
          datasets: [
            {
              label: '家电',
              data: [234, 278, 270, 190, 230]
            },
            {
              label: '百货',
              data: [164, 178, 190, 135, 160]
            },
            {
              label: '食品',
              data: [144, 198, 150, 235, 120]
            }
          ]
        },
        options2: {
          type: 'line',
          title: {
            text: '最近几个月各品类销售趋势图'
          },
          labels: ['6月', '7月', '8月', '9月', '10月'],
          datasets: [
            {
              label: '家电',
              data: [234, 278, 270, 190, 230]
            },
            {
              label: '百货',
              data: [164, 178, 150, 135, 160]
            },
            {
              label: '食品',
              data: [74, 118, 200, 235, 90 ]
            }
          ]
        }
      };
    },
    computed: {
      role() {
        return this.name === 'admin' ? '超级管理员' : '普通用户';
      }
    },
    components: {
      Schart
    }
  }
</script>

<style scoped>
  .el-row {
    margin-bottom: 20px;
  }
  .mgb20 {
    margin-bottom: 20px;
  }
  .user-avator {
    width: 120px;
    height: 120px;
    border-radius: 50%;
  }
  .user-info {
    display: flex;
    align-items: center;
    padding-bottom: 20px;
    margin-bottom: 20px;
    border-bottom: 2px solid #c8c8c8;
  }
  .user-info-cont {
    padding-left: 50px;
    font-size: 14px;
    color: #999;
    flex: 1;
  }
  .user-info-cont div:first-child {
      font-size: 30px;
      color: #222;
  }
  .user-info-name {
    font-size: 30px;
    color: black;
  }
  .user-info-list {
    font-size: 14px;
    color: #999999;
    line-height: 25px;
  }
  .user-info-list span {
    padding-left: 80px;
  }
  .grid-content {
    display: flex;
    height: 100px;
    align-items: center;
  }
  .grid-cont-right {
      flex: 1;
      text-align: center;
      font-size: 14px;
      color: #999;
  }
  .grid-con-icon {
    width: 100px;
    height: 100px;
    line-height: 100px;
    text-align: center;
    font-size: 50px;
    color: #FFFFFF;
  }
  .todo-item-del {
    text-decoration: line-through;
  }
  .grid-num {
      font-size: 30px;
      font-weight: bold;
  }
  .grid-con-1 .grid-con-icon {
      background: rgb(45, 140, 240);
  }
  .grid-con-1 .grid-num {
      color: rgb(45, 140, 240);
  }
  .grid-con-2 .grid-con-icon {
      background: rgb(100, 213, 114);
  }
  .grid-con-2 .grid-num {
      color: rgb(45, 140, 240);
  }
  .grid-con-3 .grid-con-icon {
      background: rgb(242, 94, 67);
  }

  .grid-con-3 .grid-num {
      color: rgb(242, 94, 67);
  }
  .schart {
    width: 100%;
    height: 300px;
  }
</style>
