<template>
    <div class="busserver-container">
    
    
    
        <!-- 搜索区域 -->
    
    
    
        <div solt="header" class="header">
    
    
    
            <el-input  placeholder="请搜索电话" auto-complete="on" class="search"></el-input>
    
    
    
            <el-button type="primary">搜索</el-button>
    
    
    
            <el-button type="primary">添加</el-button>
    
    
    
            <el-button type="danger">删除</el-button>
    
    
    
        </div>
    
    
    
        <el-table :data="busTable" border style="width:100%">
            <el-table-column label="序号" width="50" fixed type="index"></el-table-column>
            <el-table-column prop="date" label="日期" width="150" fixed></el-table-column>
    
            <el-table-column prop="route" label="路线名" width="150" fixed></el-table-column>
    
            <el-table-column prop="mobile" label="电话" fixed></el-table-column>
            
            <!-- 操作列 -->
            <el-table-column fixed="right" label="操作" width="100">
                <template slot-scope="scope">
                    <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
                    <el-button type="text" size="samll" @click="dialogFormVisable=true">编辑</el-button>
                    <el-dialog title="路线标题编辑" :visible.sync="dialogFormVisable">
                      <div slot="footer" class="dialog-footer">
                          <el-button @click="dialogFormVisable=false" type="primary">确认</el-button>
                          <el-button @click="dialogFormVisable=false">取消</el-button>
                      </div>
                    </el-dialog>
                </template>
            </el-table-column>
        </el-table>
    
    
    
    </div>
</template>

<script type="text/ecmascript-6">
    export default {
      data() {
        return {
          busTable: [
            {
              'date': '2018-06-6',
              'route': '宝安路线',
              'mobile': '188-8888-8888'
            },
            {
              'date': '2018-06-6',
              'route': '宝安路线',
              'mobile': '188-8888-8888'
            },
            {
              'date': '2018-06-6',
              'route': '宝安路线',
              'mobile': '188-8888-8888'
            }
          ],
          dialogFormVisable: false
        }
      },
      methods: {
        handleClick(row) {
          console.log(row)
        }
      }
    }
</script>

<style lang="scss" rel="stylesheet/scss">
    .busserver-container {
    
        margin: 20px;
    
    }
    
    
    
    .header {
    
        margin-bottom: 20px;
    
    }
    
    
    
    .search {
    
        width: 200px;
    
    }
</style>
