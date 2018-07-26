<template>
  <div class="dashboard-container">
    
   <!--<div class="dashboard-text">name:{{name}}</div>
    <div class="dashboard-text">roles:<span v-for='role in roles' :key='role'>{{role}}</span></div>-->
    
    
    <!--用户名登录展示页面-->
  
      <!-- 调查饼形图 -->
     <el-row :gutter="20">
          <el-col :xs="12" :sm="12" :md="12" :lg="12" :xl="12"><div id="main1" style="width:600px;height: 400px;"></div></el-col>
          <el-col :xs="12" :sm="12" :md="12" :lg="12" :xl="12"><div id="main2" style="width:600px;height: 400px;"></div></el-col>
     </el-row> 

  </div>

</template>

<script>
import echarts from 'echarts'
import { mapGetters } from 'vuex'

export default {
  name: 'dashboard',
  computed: {
    ...mapGetters([
      'name',
      'roles'
    ])
  },
  data() {
    return {
      charts: '',
      activeIndex2: '1',
      opinion: ['满意', '一般', '讨厌'],
      opinionData: [
        { value: 40, name: '满意' },
        { value: 366, name: '一般' },
        { value: 20, name: '讨厌' }
      ]
    }
  },
  methods: {
    handleSelect(key, keyPath) {
    },
    handleOpen(key, keyPath) {
      console.log(key, keyPath)
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath)
    },
    drawPie(id) {
      // 初始化echarts
      this.charts = echarts.init(document.getElementById(id))
      this.charts.setOption({
        title: {
          text: '9月食堂调查情况',
          // subtext: '纯属虚构',
          x: 'center'
        },
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b} : {c} ({d}%)'
        },
        legend: {
          orient: 'vertical',
          left: 'left',
          data: ['满意', '一般', '讨厌']
        },
        series: [
          {
            name: '访问来源',
            type: 'pie',
            radius: '55%',
            center: ['50%', '60%'],
            data: [
              { value: 40, name: '满意' },
              { value: 366, name: '一般' },
              { value: 20, name: '讨厌' }
            ],
            itemStyle: {
              emphasis: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: 'rgba(0, 0, 0, 0.5)'
              }
            }
          }
        ]
      })
    }
  },
  mounted() {
    this.$nextTick(function() {
      this.drawPie('main1')
      this.drawPie('main2')
    })
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
.content {
  margin-top: 20px;
}
</style>
