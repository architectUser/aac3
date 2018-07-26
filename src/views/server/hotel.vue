<template>
    <div class="hotel-container">
        <el-row :gutter="20">
            <el-col :span="6" v-for="o in 8" :key="o" >
                <el-card class="hotel-card">
                    <div slot="header" class="clearfix">
                        <span>酒店名称</span>
                    </div>
                        
                    <div class="text item pic">
                        <img src="" alt="" >
                    </div>
                    
                    <div class="footer">
                       <el-button icon="el-icon-delete" type="primary" @click="dialogFormVisable=true">删除</el-button>

                       <el-dialog title="提示" :visible.sync="dialogFormVisable">
                          <div>是否确认删除该内容？</div>
                         <el-button @click="dialogFormVisable=false" type="primary">确认</el-button>
                         <el-button @click="dialogFormVisable=false">删除</el-button>
                       </el-dialog>
                    </div>
                </el-card>
            </el-col>
        </el-row>
    </div>
</template>

<script type="text/ecmascript-6">
 export default{
   data() {
     return {
         dialogFormVisable: false
     }
   }
 }
</script>

<style lang="scss" rel="stylesheet/scss">
.hotel-container{
  margin: 20px;
} 
.hotel-card .pic{
 width: 100%;
 height: 200px;
 background: #ccc;
}
.el-col{
    margin-bottom: 20px;
}
.footer{
    margin-top: 20px;
}
</style>
