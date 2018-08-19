<template>
    <div class="editsurvery">
      <el-card>
        <el-select v-model="value" placeholder="请选择">
          <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value"  >
          
          </el-option>
        </el-select>

        <el-button type="primary" @click.native="getOption">确认提交</el-button>
      </el-card>
      <ul class="questionBox" ref="questionBox">
        <li :is="item.component" :text="index" :template="template" v-for="(item,index) in template" :key="index" >
        </li>
      </ul>
    </div>
</template>

<script type="text/ecmascript-6">
import RadioComponent from './template/radio'
import CheckboxComponent from './template/checkbox'
import InputComponent from './template/input'
export default {
  data() {
    return {
      options: [{
        value: 'RadioComponent',
        label: '单选'
      },
      {
        value: 'CheckboxComponent',
        label: '多选'
      },
      {
        value: 'InputComponent',
        label: '填空'
      }],
      value: '',
      hidden: false,
      template: []
    }
  },
  methods: {
    // 选择相应的下拉选项框对应相应的模板
    getOption() {
      console.log('this.value' + this.value);
      console.log(1);
      this.add(this.value);
    },
    // 添加模板
    add(component){
      //console.log(this.template)
      this.template.push({
        'component': component
      })
    },
    // 删除模板
    remove(){
      console.log(1);
      // this.template.splice(index, 1)
    }
  
  },
  components: {
    'RadioComponent': RadioComponent,
    'CheckboxComponent': CheckboxComponent,
    'InputComponent': InputComponent
  }
}
</script>


<style lang="scss" rel="stylesheet/scss">
.question-wrap{
  margin: 10px;
}
.margintop{
  margin-top: 10px;
}
.edit{
  border: 1px solid #ddd;
  padding: 20px;
  border-radius: 5px;
}
.edit-wrap{
  width: 100%;
  overflow: hidden;
  div{
    float: left;
    width: 50%;
    text-align: center;
    height: 40px;
    line-height: 40px;
  }
  .cancle{
    background: #f3f46e;
  }
  .finish{
    border-left: 0px;
    color:#fff;
    background: #3a8ee6;
  }
}
.questionBox{
  margin: 0;
  padding: 0;
}    
</style>