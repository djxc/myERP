// 主页界面
<template>
  <div class="dashboard-container">
    <!-- <div class="dashboard-text">name: {{ name }}</div> -->
    <div class="dashboard-mainPage">
      <div class="dashboard-mainPage-tongji">
        <div class="dashboard-mainPage-tongji-xiaoshou">
          <p>销售统计</p>
          <hr>
          <el-table :data="saleDataDay" style="width: 100%" :show-header="showHead">
            <el-table-column align="center" prop="type">               
              </el-table-column>
              <el-table-column align="center" prop="value">              
              </el-table-column>
              <el-table-column align="center" prop="unit">               
              </el-table-column>               
          </el-table>          
          <hr>   
          <el-table :data="saleData" style="width: 100%" :show-header="showHead">
            <el-table-column align="center" prop="type">               
              </el-table-column>
              <el-table-column align="center" prop="value">              
              </el-table-column>
              <el-table-column align="center" prop="unit">               
              </el-table-column>               
          </el-table>            
        </div>
        <div class="dashboard-mainPage-tongji-huikuan">
          <p>本年回款统计</p>
          <hr>
          <div class="dashboard-mainPage-tongji-huikuan-table1">
            <el-table :data="huikuanData" style="width: 100%" :show-header="showHead">
              <el-table-column align="center" prop="type">               
                </el-table-column>
                <el-table-column  align="center" prop="value">              
                </el-table-column>
                <el-table-column align="center" prop="unit">               
                </el-table-column>               
            </el-table>          
          </div>
          <hr>
          <el-table :data="tableData" style="width: 100%" height="70%" show-summary :summary-method="getSummaries">
             <el-table-column align="center" label="序号" prop="id" sortable>               
              </el-table-column>
              <el-table-column label="姓名" prop="name">              
              </el-table-column>
              <el-table-column label="电话" align="center" prop="phoneNum">               
              </el-table-column>
              <el-table-column label="金额" align="center" prop="money" sortable>               
              </el-table-column>
          </el-table>
        </div>
        <div class="dashboard-mainPage-tongji-qiankuan">
          <p>本年欠款统计</p>
          <hr>
          <div class="dashboard-mainPage-tongji-huikuan-table1">
            <el-table :data="quikuanData" style="width: 100%" :show-header="showHead">
              <el-table-column align="center" prop="type">               
                </el-table-column>
                <el-table-column align="center" prop="value">              
                </el-table-column>
                <el-table-column align="center" prop="unit">               
                </el-table-column>               
            </el-table>               
          </div>
          <hr>          
          <el-table :data="tableData" style="width: 100%" height="70%" show-summary :summary-method="getSummaries">
             <el-table-column align="center" label="序号" prop="id" sortable>               
              </el-table-column>
              <el-table-column label="姓名" prop="name">              
              </el-table-column>
              <el-table-column label="电话" align="center" prop="phoneNum">               
              </el-table-column>
              <el-table-column label="金额" align="center" prop="money" sortable>               
              </el-table-column>
          </el-table>
        </div>
      </div>
      <hr>
      <div class="dashboard-mainPage-workStats">
        <!-- 当前工作状态 -->
          <el-table :data="orderStatus" style="width: 100%">
             <el-table-column align="center" label="排单中" prop="waitingOrder">               
              </el-table-column>
              <el-table-column label="已下单" align="center" prop="readyOrder">              
              </el-table-column>
              <el-table-column label="车间未接受" align="center" prop="notAcceptOrder">               
              </el-table-column>
              <el-table-column label="车间生产中" align="center" prop="producting">               
              </el-table-column>
              <el-table-column label="生产已完成" align="center" prop="producted">               
              </el-table-column>
              <el-table-column label="待结算订单" align="center" prop="settlementOrder">               
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
        ],
        huikuanData: [
          {
            type: "当前未回款总额：",
            value: 120,
            unit: '元'
          },
          {
            type: "当年未回款总额：",
            value: 120,
            unit: '元'
          },
          {
            type: "以往未回款总额：",
            value: 120,
            unit: '元'
          }
        ],
        saleData: [{
          type: '当月销售额：',
          value: 120,
          unit: '元'
        },{
          type: '上月销售额：',
          value: 120,
          unit: '元'
        },{
          type: '当月销售单：',
          value: 120,
          unit: '单'
        },{
          type: '上月销售单：',
          value: 120,
          unit: '单'
        }],
        saleDataDay: [
        {
          type: '当日销售额：',
          value: 120,
          unit: '元'
        },
        {
          type: '昨日销售额：',
          value: 120,
          unit: '元'
        },
        {
          type: '当日销售单：',
          value: 120,
          unit: '单'
        },
        {
          type: '昨日销售单：',
          value: 120,
          unit: '单'
        }],
        quikuanData: [{
          type: '当前未回款总额：',
          value: 120,
          unit: '元'
        },{
          type: '当年未回款总额：',
          value: 120,
          unit: '元'
        },{
          type: '以往未回款总额：',
          value: 120,
          unit: '元'
        }],
        showHead: false
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
    height: 100%;
    min-height: calc(80vh - 50px);
    margin: 1%;
    margin-top: 0%;
  }
  &-text {
    font-size: 10px;
    line-height: 16px;
  }
  &-mainPage {
    height: 100%;
    &-tongji {
      background-color: rgb(252, 252, 252);      
      height: 80%;
      min-height: calc(60vh);
      &-xiaoshou, &-huikuan,&-qiankuan {
        margin-left: 1%;
        width: 32%;
        height: 80%;
        float: left;
        text-align: center;
      }
     p{
        font-size: 1.2em;
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
      background-color: rgb(255, 254, 254);
      text-align: center;
      height: 20%;
      font-size: 1.5em;
    }
  }
}

</style>
