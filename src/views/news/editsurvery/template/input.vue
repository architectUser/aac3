<template>
    <div class="input wrap"  @mouseover="showBtn=true" @mouseout="showBtn=false">
          <el-card class="margintop question-wrap input-wrap" v-show="radioQuestion" ref="inputWrap">
        <div class="btn-area" v-show="showBtn">
            <el-button size="small" type="primary" @click="upmove">上移</el-button>
            <el-button size="small" type="primary" @click="downmove">下移</el-button>
            <el-button size="small" type="primary" @click="showwrap=!showwrap">编辑</el-button>
            <el-button size="small" type="primary" @click="remove" >删除</el-button>
        </div>

       <!-- 多选编辑完成区域-->
       <div class="radioFinish" ref="radioFinish">
          <h4 ref="h4"><span>{{text+1}}.</span>{{question}}<span>【提问】</span></h4>
          <div v-for="item in inputItems" :key="item.value">
            <el-input>{{item.input}}</el-input>
          </div>
       </div>

        <!-- 提问编辑区域 -->
       <div class="edit margintop" v-show="showwrap" ref="edit">
          <div class="question-area margintop">
            <el-input type="textarea" placeholder="请编辑问题？" v-model="question" ></el-input>
            <div v-for="(item, index) in inputItems" :key="item.value" class="margintop radioChoose" id="radioChoose">
                <el-radio :label="index" v-model="radio">
                  <el-input type="text"  v-model="item.input" placeholder="【提问】"></el-input>
                    <el-button size="small" type="primary" class="delete" @click="deleteChoose(index)">删除</el-button>
                </el-radio>
              
            </div>
          </div>
          
          <div class="edit-wrap margintop">
            <div class="cancle" @click="showwrap=!showwrap">取消编辑</div><div class="finish"  @click="finshEdit">完成编辑</div>
          </div>

       </div>
      </el-card>
 </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    text: null,
    template: null
  },
  data() {
    return {
      showBtn: false,
      radio: '1',
      radioQuestion: true,
      showwrap: true,
      question: '',
      inputItems: [{ // 单选模板
        'input': '【单选】',
        'isChoose': false
      }],
      newItem: {
        'input': '【单选】',
        'isChoose': false
      },
      value: '',
      hidden: false
    }
  },
  methods: {
    // 增加选项
    addChoose() {
      this.inputItems.push(this.newItem)
      this.newItem = { 'input': '【单选】', 'isChoose': false } // 注意这个一定要重置
    },
    // 删除选项
    deleteChoose(index) {
      this.inputItems.splice(index, 1)
    },
    // 取消编辑
    cancleEdit() {
      this.$forceUpdate()
      this.showwrap = !this.showwrap
    },
    // 完成编辑
    finshEdit(event) {
      this.hidden = true
      this.showwrap=!this.showwrap
    },
    // 删除编辑区域
    remove() {
        let index = this.text;
        this.template.splice(index,1);
    },
    // 上移编辑区域
    upmove(){
        let index = this.text
        let arr = this.template[index]
        if (index > 1) {
         this.$set(this.template, index, this.template[index - 1])
         this.$set(this.template, index - 1, arr)
        } 
    },
    // 下移编辑区域
    downmove() {
      const index = this.text
      const arr = this.template[index]
      if (index < this.template.length - 1) {
          this.$set(this.template, index, this.template[index+1])
          this.$set(this.template, index + 1, arr)
      }
    },
    // 选择相应的下拉选项框对应相应的模板
    getOption() {
      console.log('this.value' + this.value)
      // 获取到box的标签类名
      console.log(this.$refs.radioWrap)
    }
  }
}
</script>


<style lang="scss" rel="stylesheet/scss">
.wrap{
    position: relative;
}
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
.btn-area{
    position: absolute;
    right: 30px;
    top: 20px;
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

</style>