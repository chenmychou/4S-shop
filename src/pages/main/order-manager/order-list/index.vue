<template>
  <div class="baoyang_order_pages">
    <div class="tab_change_list">
      <div
        @click="changeClick(item)"
        v-for="item in tabList"
        :key="item.tabName"
        class="item_tab"
        :class="item.isActive ? 'isTabClick' : 'notClick'">
        {{item.tabName}}
      </div>
    </div>
    <div class="order_list_content">
      <div class="order_item_card" v-for="(info, index) in orderList" :key="index">
        <div class="head_title">
          <div class="_left_title">
            保养预约
          </div>
          <div class="_right_status">
            {{orderStatusMap[info.status]}}
          </div>
        </div>
        <div class="center_content" @click="checkOrderDetail()">
          <div class="company_name_info">
            <div class="company_name">
              {{info.companyName}}
            </div>
            <div class="money_count">
              ¥ {{info.money}}
            </div>
          </div>
          <div class="car_brand">
            {{info.placeBrand}}（{{info.rangeMile}}）
          </div>
          <div class="yuyue_info">
            <div class="yuyue_date">
              预约时间：{{info.datetime}}
            </div>
            <div class="yuyue_SA">
              预约SA：{{info.saName}}
            </div>
          </div>
        </div>
        <div class="order_status_btn">
          <div
            class="new_creat_btn btn_common"
            v-if="info.status === 1 || info.status === 2 || info.status === 3 || info.status === 4">
            取消订单
          </div>
          <div
            v-if="info.status === 1"
            class="cancle_btn btn_common canClick">
            更改时间
          </div>
          <div
            v-if="info.status === 4"
            class="cancle_btn btn_common canClick">
            确认作业
          </div>
          <div
            v-if="info.status === 3 || info.status === 4 || info.status === 5 || info.status === 6 || info.status === 7 || info.status === 11 || info.status === 12 || info.status === 13"
            class="change_date_btn btn_common canClick" @click="checkCarOrder()">
            车检报告
          </div>
          <div
            v-if="info.status === 1 || info.status === 2"
            class="navigetor_go btn_common canClick">
            导航前往
          </div>
          <div
            v-if="info.status === 5 || info.status === 6 || info.status === 11 || info.status === 12 || info.status === 13"
            class="navigetor_go btn_common canClick">
            作业进度
          </div>
          <div
            v-if="info.status === 7 || info.status === 8 || info.status === 9"
            class="navigetor_go btn_common canClick">
            保养报告
          </div>
          <div
            v-if="info.status === 8"
            class="navigetor_go btn_common canClick">
            待评价
          </div>
          <div
            v-if="info.status === 7"
            class="navigetor_go btn_common canClick">
            确认结算
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {
  },
  data () {
    return {
      tabList: [
        {
          tabName: '全部',
          id: 1,
          isActive: true
        },
        {
          tabName: '服务中',
          id: 2,
          isActive: false
        },
        {
          tabName: '待评价',
          id: 3,
          isActive: false
        }
      ],
      orderStatusMap: {
        1: '已预约', // 取消 改时间 导航
        2: '已接单', // 取消 导航
        3: '检测中', // 取消 车检报告
        4: '待用户确认', // 取消 车检报告 确认作业
        5: '作业中', // 车检报告 作业进度
        6: '作业中', // 车检报告 作业进度
        7: '完成待确认', // 车检报告 保养报告 确认结算
        8: '待评价', // 保养报告 待评价
        9: '完成', // 保养报告
        10: '已取消', // 无
        11: '作业中', // 车检报告 作业进度
        12: '作业中', // 车检报告 作业进度
        13: '作业中' // 车检报告 作业进度
      },
      orderList: [
        {
          status: 1,
          money: 1999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 2,
          money: 2999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 3,
          money: 1888,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 4,
          money: 1999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 5,
          money: 2999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 6,
          money: 1888,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 7,
          money: 1999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 8,
          money: 2999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 9,
          money: 1888,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 10,
          money: 1999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 11,
          money: 2999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 12,
          money: 1888,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        },
        {
          status: 13,
          money: 1999,
          rangeMile: 5000,
          companyName: '长沙一汽大众4S店销售服务有限公司',
          placeBrand: '湘AH88X0',
          datetime: '2018-11-26 09:30',
          saName: '老张沙雕'
        }
      ]
    }
  },
  methods: {
    changeClick (info) {
      // this.tabList.map(ele => ele.isActive = false)
      let tabLists = this.tabList
      let tempArr = []
      tabLists.forEach(item => {
        if (item.id === info.id) {
          item.isActive = true
        } else {
          item.isActive = false
        }
        tempArr.push(item)
      })
      this.tabList = tempArr
    },
    checkOrderDetail (id) {
      wx.navigateTo({
        url: '../order-detail/main'
      })
    },
    checkCarOrder () {
      wx.navigateTo({
        url: '../check-car/main'
      })
    }
  },
  onShow () {
  },
  onLoad () {
    // 解决页面返回后，数据没重置的问题
    Object.assign(this, this.$options.data())
  }
}
</script>

<style>
  .order_status_btn{
    display: flex;
    justify-content:flex-end;
    align-items: center;
    height: 98rpx;
    line-height: 98rpx;
    padding: 0 22rpx 0 36rpx;
  }
  .order_status_btn .canClick{
    background: #568FF4 !important
  }
  .order_status_btn .btn_common{
    margin-left: 30rpx;
    line-height: 54rpx;
    text-align: center;
    font-size:28rpx;
    font-weight:400;
    color:rgba(255,255,255,1);
    width:140rpx;
    height:54rpx;
    background:rgba(207,207,207,1);
    border:1rpx solid rgba(207,207,207,1);
    border-radius:4rpx;
  }
  .order_status_btn .fixed_btn{
    width: 140rpx;
  }
  .order_status_btn .change_date_btn{
    
  }
  .order_status_btn .navigetor_go{
    
  }


  .order_list_content{
    
  }
  .order_list_content .order_item_card{
    /* 订单列表卡片 */
    margin-bottom: 10rpx;
    height: 510rpx;
    background:rgba(255,255,255,1);
    box-shadow:0rpx 4rpx 8rpx 0rpx rgba(138,140,144,0.57);
  }
  .order_item_card .head_title{
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 88rpx;
    line-height: 88rpx;
    padding: 0 22rpx 0 36rpx;
    border-bottom: 2rpx solid #f4f4f4;
  }
  .head_title ._left_title{
    font-size:24rpx;
    font-weight:400;
    color:rgba(153,153,153,1);
  }
  .head_title ._right_status{
    font-size:24rpx;
    font-weight:400;
    color:rgba(86,143,244,1);
  }
  .center_content {
    height: 320rpx;
    padding: 0 22rpx 0 36rpx;
    border-bottom: 2rpx solid #f4f4f4;
  }
  .center_content .company_name_info{
    padding-top: 32rpx;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .center_content .company_name_info .company_name{
    font-size:32rpx;
    font-weight:400;
    color:rgba(0,0,0,1);
  }
   .center_content .company_name_info .money_count{
    line-height: 2.5;
    font-size:32rpx;
    font-weight:400;
    color:rgba(255,0,0,1);
  }
  .center_content .car_brand{
    padding-top: 50rpx;
    font-size:28rpx;
    font-weight:400;
    color:rgba(51,51,51,1);
  }
  .center_content .yuyue_info{
    padding-bottom: 56rpx;
    padding-top: 56rpx;
    font-size:28rpx;
    font-weight:400;
    color:rgba(51,51,51,1);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

.baoyang_order_pages{

}
.tab_change_list{
  display: flex;
  background: #568FF4;
  justify-content: space-between;
  align-items: center;
  padding: 0 84rpx 0 98rpx;
  height: 78rpx;
  line-height: 60rpx;
}
.tab_change_list .isTabClick{
  border-bottom: 4rpx solid #f4f4f4;
}
.tab_change_list .item_tab{
  margin-bottom: 10rpx;
  font-size:28rpx;
  font-weight:400;
  color:rgba(255,255,255,1);
}
.tab_change_list .notClick{
  opacity:0.4;
}
</style>
