<template>
  <div class="mobile-container">
  
    <!-- 搜索区域 -->
  
    <div solt="header" class="header">
  
      <el-input v-model="serach" placeholder="请搜索电话" auto-complete="on" class="search"></el-input>
  
      <el-button type="primary">搜索</el-button>
  
      <el-button type="primary">添加</el-button>
  
      <el-button type="danger">删除</el-button>
  
    </div>
  
  
  
    <!-- 搜索分类 -->
  
    <el-tabs v-model="activeName" @tab-click="handleClick">
  
      <el-tab-pane label="常用电话" name="usually">
  
        <el-table :data="tableData" style="width: 100%" :row-class-name="tableRowClassName">
          
          <el-table-column type="selection" width="55">

          </el-table-column>

          <el-table-column prop="date" label="日期" width="180">
  
          </el-table-column>
  
          <el-table-column prop="name" label="姓名" width="180">
  
          </el-table-column>
  
          <el-table-column prop="mobile" label="电话">
  
          </el-table-column>

          <el-table-column prop="position" label="职位">
  
          </el-table-column>
          <!-- 操作列 -->
            <el-table-column fixed="right" label="操作" width="100">
                <template slot-scope="scope">
                    <el-button @click="handleClickDetail(scope.row)" type="text" size="small">查看</el-button>
                    <el-button type="text" size="samll" @click="dialogForm(scope.row)">编辑</el-button>

                </template>
            </el-table-column>
        </el-table>
             
            <el-dialog title="路线标题编辑" :visible.sync="dialogFormVisable">
                       <el-form ref="rotuerform" :model="rotuerform" label-width="120px">
                        <el-form-item label="联系电话">
                          <el-input v-model="rotuerform.mobile"></el-input>
                        </el-form-item>
                        <el-form-item label="联系人">
                           <el-input v-model="rotuerform.name"></el-input>
                        </el-form-item>
                       </el-form>
                      <div slot="footer" class="dialog-footer">
                          <el-button @click="confirm(current)" type="primary">确认</el-button>
                          <el-button @click="dialogFormVisable=false">取消</el-button>
                      </div>
            </el-dialog>       
        <el-pagination @size-change="handleSizeChange" @current-change="handleCurrentChange" :current-page="currentPage1" :page-sizes="[100, 200, 300, 400]"
       :page-size="100" layout="total, sizes, prev, pager, next, jumper" :total="400">

        </el-pagination>
      </el-tab-pane>
  
      <el-tab-pane label="司机电话" name="car">
          
        <el-table :data="tableData" style="width: 100%">
  
          <el-table-column prop="date" label="日期" width="180">
  
          </el-table-column>
  
          <el-table-column prop="name" label="姓名" width="180">
  
          </el-table-column>
  
          <el-table-column prop="mobile" label="电话">
  
          </el-table-column>

          <el-table-column prop="position" label="职位">
  
          </el-table-column>

        </el-table>

        <el-pagination @size-change="handleCurrentChange" @current-change="handleCurrentChange" :current-page="currentPage2" :page-sizes="[100, 200, 300, 400]"
        :page-size="100" layout="total, sizes, prev, pager, next, jumper" :total="400"></el-pagination>
      </el-tab-pane>
  
      <el-tab-pane label="服务电话" name="survery">
          
        <el-table :data="tableData" style="width: 100%">
  
          <el-table-column prop="date" label="日期" width="180">
  
          </el-table-column>
  
          <el-table-column prop="name" label="姓名" width="180">
  
          </el-table-column>
  
          <el-table-column prop="mobile" label="电话">
  
          </el-table-column>

          <el-table-column prop="position" label="职位">
  
          </el-table-column>

        </el-table>

        <el-pagination @size-change="handleCurrentChange" @current-change="handleCurrentChange" :current-page="currentPage3" :page-sizes="[100, 200,300, 400]"
        :page-size="100" layout="total, sizes, prev, pager, next, jumper" :total="400"></el-pagination>
      </el-tab-pane>
  
      <el-tab-pane label="行政电话" name="adminstaff">
          
        <el-table :data="tableData" style="width: 100%">
  
          <el-table-column prop="date" label="日期" width="180">
  
          </el-table-column>
  
          <el-table-column prop="name" label="姓名" width="180">
  
          </el-table-column>
  
          <el-table-column prop="mobile" label="电话">
  
          </el-table-column>

          <el-table-column prop="position" label="职位">
  
          </el-table-column>

        </el-table>

        <el-pagination @size-change="handleCurrentChange" @current-change="handleCurrentChange" :current-page="currentPage4" :page-sizes="[100, 200,300, 400]"
        :page-size="100" layout="total, sizes, prev, pager, next, jumper" :total="400"></el-pagination>
      </el-tab-pane>
  
    </el-tabs>
  

  </div>
</template>

<script>
  export default {
  
    data() {
      return {
        serach: '',
        activeName: 'usually',
        currentPage1: 1,
        currentPage2: 1,
        currentPage3: 1,
        currentPage4: 1,
        current: '',
        tableData: [{
          'date': '2018-07-26',
          'name': '程咬金',
          'mobile': '188-8888-8888',
          'position': '司机'
        },
        {
          'date': '2018-07-26',
          'name': '程咬金',
          'mobile': '188-8888-8888',
          'position': 'HR'
        },
        {
          'date': '2018-07-26',
          'name': '程咬金',
          'mobile': '188-8888-8888',
          'position': 'HR'
        },
        {
          'date': '2018-07-26',
          'name': '程咬金',
          'mobile': '188-8888-8888',
          'position': 'HR'
        },
        {
          'date': '2018-07-26',
          'name': '程咬金',
          'mobile': '188-8888-8888',
          'position': 'HR'
        }
        ],
        dialogFormVisable: false,
        rotuerform:
          {
            name: '',
            mobile: ''
          }
      }
    },
    methods: {
      handleClick(tab, event) {
        console.log(tab, event)
      },
      handleClickDetail(row) {
        alert(0)
        console.log(row)
      },
      handleSizeChange(val) {
        console.log(`每页 ${val} 条`)
      },
      handleCurrentChange(val) {
      },
      dialogForm(row) {
        this.dialogFormVisable = true
        this.rotuerform.mobile = row.mobile
        this.rotuerform.name = row.name
        // 获取当前行的索引值
        console.log(row.index)
        this.current = row.index
      },
      confirm() {
        this.tableData[this.current].mobile = this.rotuerform.mobile
        this.tableData[this.current].name = this.rotuerform.name
        this.dialogFormVisable = false
      },
      tableRowClassName ({row, rowIndex}) {
        //把每一行的索引放进row
        row.index = rowIndex;
      }
    }
  }
</script>

<style lang="scss" rel="stylesheet/scss" scoped>
  .mobile-container {
  
    margin: 20px;
  
  }
  
  
  
  .header {
  
    margin-bottom: 20px;
  
  }
  
  
  
  .search {
  
    width: 200px;
  
  }
  .el-pagination{
    margin-top: 20px;
  }
</style>
