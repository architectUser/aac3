<template>
<div class="satisfied-contianter">
    <!-- 调查问卷定义 -->
    <el-input placeholder="问卷标题"></el-input>
    <el-button >添加试题</el-button>
    <!-- 编辑试题-->
    <el-form ref="form" :model="form" label-width="120px">
      <el-form-item label="问题">
        <el-input v-model="form.question"></el-input>
      </el-form-item>
      <el-form-item label="活动主题">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="活动地区">
        <el-select v-model="form.region" placeholder="please select your zone">
          <el-option label="Zone one" value="上海"></el-option>
          <el-option label="Zone two" value="北京"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="活动时间">
        <el-col :span="11">
          <el-date-picker type="date" placeholder="Pick a date" v-model="form.date1" style="width: 100%;"></el-date-picker>
        </el-col>
        <el-col class="line" :span="2">-</el-col>
        <el-col :span="11">
          <el-time-picker type="fixed-time" placeholder="Pick a time" v-model="form.date2" style="width: 100%;"></el-time-picker>
        </el-col>
      </el-form-item>
      <el-form-item label="启用">
        <el-switch v-model="form.delivery"></el-switch>
      </el-form-item>
    </el-form>
    <div class="question">
        <el-card class="box-card">
            <div slot="header" class="clearfix">
                <span>问题</span>
                <el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button>
            </div>
            <div v-for="o in 4" :key="o" class="text item">
                {{'答案 ' + o }}
            </div>
       </el-card>
    </div>
</div>

</template>

<script type="text/ecamscript-6">
    
</script>

<style rel="stylesheet/scss" lang="scss">

</style>

