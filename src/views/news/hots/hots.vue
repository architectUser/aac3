<template>
  <div class="hots-container">
    <div solt="header" class="header">
        <el-input v-model="input" placeholder="请搜索公告标题" auto-complete="on" class="search"></el-input>
        <el-button type="primary">搜索</el-button>
        <el-button type="primary">添加</el-button>
        <el-button type="danger">删除</el-button>
    </div>
    
    <!-- 公告列表展示页 -->
    <el-row :gutter="20">
        <el-col :xs="8" :sm="6" :md="6" :lg="6" :xl="6" v-for="n in 4" :key="n">
            <el-card class="" @click.native="gotoEditAd">
                <div slot="header" class="clearfix">
                    <span>公告标题</span>
                    <el-button style="float: right; padding: 3px 0" type="text" @click="dialogFormVisible = true">编辑</el-button>

                    <!-- 编辑页面弹窗 -->
                    <el-dialog title="公告编辑页面" :visible.sync="dialogFormVisible">
                        <el-form :model="form">
                            <el-form-item label="公告标题" :laber-width="formLabelWidth">
                                <el-input v-model="form.title" auto-complete="off"></el-input>
                            </el-form-item>
                            <el-form-item label="公告内容" :laber-width="formLabelWidth">
                                <el-input v-model="form.content" auto-complete="off"></el-input>
                            </el-form-item>
                        </el-form>
                        <div solt="footer" class="dialog-footer">
                            <el-button @click="dislogFormVisible=false">取消</el-button>
                            <el-button @click="dislogFormVisible=false" type="primary">确定</el-button>
                        </div>
                    </el-dialog>
                </div>
                <div class="text item pic">
                    <img src="" alt="" >
                </div>
            </el-card>
        </el-col>
    </el-row>

  </div>

</template>

<script>
export default {
  data() {
    return {
      dialogFormVisible: false,
      form: {
        title: '',
        content: ''
      },
      formLabelWidth: '120px'
    }
  },
  methods: {
    gotoEditAd() {
      this.$router.push({ path: '/editAd' })
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.text {
font-size: 14px;
}

.item {
margin-bottom: 18px;
}

.clearfix:before,
.clearfix:after {
display: table;
content: "";
}
.clearfix:after {
clear: both
}

.box-card {
width: 480px;
}

.hots-container{
    margin: 20px;
}

.pic{
   width: 100%;
   height: 200px;
   background: #ccc;
}

.header{
    margin-bottom: 20px;
}
.search{
  width: 200px;
}
</style>
