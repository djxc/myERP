// 主页界面
<template>
  <div class="dashboard-container">
    <!-- <div class="dashboard-text">name: {{ name }}</div> -->
    <div class="dashboard-mainPage">
      <div class="dashboard-mainPage-tongji">
        <div class="dashboard-mainPage-tongji-xiaoshou">
          销售统计   
          <hr>
            <table border="1">
              <tbody>
                <tr>
                  <td>当日销售额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
                <tr>
                  <td>当日销售额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
                <tr>
                  <td>当日销售单：</td>
                  <td>120</td>
                  <td>单</td>
                </tr>
                <tr>
                  <td>昨日销售单：</td>
                  <td>120</td>
                  <td>单</td>
                </tr>
              </tbody>
            </table>
            <hr>   
             <table border="1">
              <tbody>
                <tr>
                  <td>当月销售额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
                <tr>
                  <td>上月销售额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
                <tr>
                  <td>当月销售单：</td>
                  <td>120</td>
                  <td>单</td>
                </tr>
                <tr>
                  <td>上月销售单：</td>
                  <td>120</td>
                  <td>单</td>
                </tr>
              </tbody>
            </table>
        </div>
        <div class="dashboard-mainPage-tongji-huikuan">
          本年回款统计
          <hr>
          <div class="dashboard-mainPage-tongji-huikuan-table1">
            <table border="1">
              <tbody>
                <tr>
                  <td>当前未回款总额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
                <tr>
                  <td>当年未回款总额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
                <tr>
                  <td>以往未回款总额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
              </tbody>
            </table>
          </div>
          <hr>
          <el-table :data="tableData" style="width: 100%" height="75%" show-summary :summary-method="getSummaries">
             <el-table-column align="center" label="序号" width="95" prop="id" sortable>               
              </el-table-column>
              <el-table-column label="姓名" width="95" prop="name">              
              </el-table-column>
              <el-table-column label="电话" width="200" align="center" prop="phoneNum">               
              </el-table-column>
              <el-table-column label="金额" width="150" align="center" prop="money" sortable>               
              </el-table-column>
          </el-table>
        </div>
        <div class="dashboard-mainPage-tongji-qiankuan">
          本年欠款统计
          <hr>
          <div class="dashboard-mainPage-tongji-huikuan-table1">
            <table border="1">
              <tbody>
                <tr>
                  <td>当前未回款总额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
                <tr>
                  <td>当年未回款总额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
                <tr>
                  <td>以往未回款总额：</td>
                  <td>120</td>
                  <td>元</td>
                </tr>
              </tbody>
            </table>
          </div>
          <hr>          
          <el-table :data="tableData" style="width: 100%" height="75%" show-summary :summary-method="getSummaries">
             <el-table-column align="center" label="序号" width="95" prop="id" sortable>               
              </el-table-column>
              <el-table-column label="姓名" width="95" prop="name">              
              </el-table-column>
              <el-table-column label="电话" width="200" align="center" prop="phoneNum">               
              </el-table-column>
              <el-table-column label="金额" width="150" align="center" prop="money" sortable>               
              </el-table-column>
          </el-table>
        </div>
      </div>
      <div class="dashboard-mainPage-workStats">
        当前工作状态     
          <el-table :data="orderStatus" style="width: 100%" height="80%">
             <el-table-column align="center" label="排单中" width="260" prop="waitingOrder">               
              </el-table-column>
              <el-table-column label="已下单" width="260" align="center" prop="readyOrder">              
              </el-table-column>
              <el-table-column label="车间未接受" width="260" align="center" prop="notAcceptOrder">               
              </el-table-column>
              <el-table-column label="车间生产中" width="260" align="center" prop="producting">               
              </el-table-column>
              <el-table-column label="生产已完成" width="260" align="center" prop="producted">               
              </el-table-column>
              <el-table-column label="待结算订单" width="260" align="center" prop="settlementOrder">               
              </el-table-column>
          </el-table>  
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  computed: {
    ...mapGetters([
      'name'
    ])
  },
  data() {
      return {
        tableData: [
        {
          id: 1,
          name: '王小虎',
          phoneNum: '18364356214',
          money: 326
        }, {
          id: 2,
          name: '王小虎',
          phoneNum: '18364356214',
          money: 426
        }, {
          id: 3,
          name: '王小虎',
          phoneNum: '18364356214',
          money: 376
        }, {
          id: 4,
          name: '王小虎',
          phoneNum: '18364356214',
          money: 226
        },{
          id: 5,
          name: '王小虎',
          phoneNum: '18364356214',
          money: 152
        }],
        orderStatus: [
          {
            waitingOrder: 10,
            readyOrder: 15,
            notAcceptOrder: 13,
            producting: 8,
            producted: 6,
            settlementOrder: 20
          }
        ]
      }
    },
    methods: {
      // 自定义对table进行统计
      getSummaries(param) {
        const { columns, data } = param;
        const sums = [];
        columns.forEach((column, index) => {
          if (index === 0) {
            sums[index] = '总价';
            return;
          }
          const values = data.map(item => Number(item[column.property]));
          if (!values.every(value => isNaN(value))) {
            sums[index] = values.reduce((prev, curr) => {
              const value = Number(curr);
              if (!isNaN(value)) {
                return prev + curr;
              } else {
                return prev;
              }
            }, 0);
            sums[index] += ' 元';
          } else {
            sums[index] = '';
          }
        });

        return sums;
      }
    }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    position: relative;
    min-height: calc(80vh - 50px);
    margin: 30px;
  }
  &-text {
    font-size: 10px;
    line-height: 16px;
  }
  &-mainPage {
    height: 100%;
    &-tongji {
      background-color: rgb(245, 242, 238);      
      height: 50%;
      min-height: calc(60vh);
      &-xiaoshou, &-huikuan,&-qiankuan {
        margin-left: 1%;
        width: 32%;
        height: 60vh;
        float: left;
        text-align: center;
        border-width: 0.05em;
        border-color: rgb(185, 185, 185);
        border-style: solid;
      }
      &-huikuan {
        &-table1 {
          float: center;
          text-align: center;
          background-color: rgb(247, 248, 248);
        }
      }
    }
    &-workStats {
      background-color: whitesmoke;
      text-align: center;
      height: 15vh;
    }
  }
}
</style>
