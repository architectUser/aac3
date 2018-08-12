<template>
    <div class="editsurvery">
      <el-card>
        <el-select v-model="value" placeholder="请选择">
          <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value">
          
          </el-option>
        </el-select>

        <el-button type="primary" @click="radioQuestion=!radioQuestion">确认提交</el-button>
      </el-card>
      
      <!-- 单选-->
      <el-card class="margintop question-wrap" v-show="radioQuestion" ref="questionWrap">
        <div class="btn-area">
          <el-button size="small" type="primary">上移</el-button>
          <el-button size="small" type="primary">下移</el-button>
          <el-button size="small" type="primary"  @click="showwrap=!showwrap">编辑</el-button>
          <el-button size="small" type="primary"  @click="removeChoose" >删除</el-button>
        </div>

       <!-- 单选编辑完成区域-->
       <div class="radioFinish" ref="radioFinish">
          <h4 ref="h4">{{question}}<span>【单选】</span></h4>
          <div v-for="item in items" :key="item.value">
            <el-radio>{{item.input}} <el-input  v-if="item.isChoose"></el-input></el-radio>
          </div>
       </div>

        <!-- 单选编辑区域 -->
       <div class="edit margintop" v-show="showwrap" ref="edit">
          <div class="question-area margintop">
            <el-input type="textarea" placeholder="请编辑问题？" v-model="question" ></el-input>
            <div v-for="(item, index) in items" :key="item.value" class="margintop radioChoose" id="radioChoose">
                <el-radio :label="index" v-model="radio">
                  <el-input type="text"  v-model="item.input" placeholder="【单选】"></el-input>
                    <el-radio  label="choose" v-model="item.isChoose">可填空</el-radio>
                    <el-button size="small" type="primary" class="delete" @click="deleteChoose(index)">删除</el-button>
                </el-radio>
              
            </div>

            <el-button size="small" type="primary" class="margintop addchoose" @click="addChoose">增加选项</el-button>
          </div>
          
          <div class="edit-wrap margintop">
            <div class="cancle" @click="showwrap=!showwrap">取消编辑</div><div class="finish" @click="finshEdit">完成编辑</div>
          </div>

       </div>
      </el-card>


     <!-- 多选-->
     <el-card class="margintop question-wrap" v-show="radioQuestion" ref="questionWrap">
        <div class="btn-area">
          <el-button size="small" type="primary">上移</el-button>
          <el-button size="small" type="primary">下移</el-button>
          <el-button size="small" type="primary"  @click="showwrap=!showwrap">编辑</el-button>
          <el-button size="small" type="primary"  @click="removeChoose" >删除</el-button>
        </div>

       <!-- 单选编辑完成区域-->
       <div class="radioFinish" ref="radioFinish">
          <h4 ref="h4">{{question}}<span>【单选】</span></h4>
          <div v-for="item in items" :key="item.value">
            <el-radio>{{item.input}} <el-input  v-if="item.isChoose"></el-input></el-radio>
          </div>
       </div>

        <!-- 单选编辑区域 -->
       <div class="edit margintop" v-show="showwrap" ref="edit">
          <div class="question-area margintop">
            <el-input type="textarea" placeholder="请编辑问题？" v-model="question" ></el-input>
            <div v-for="(item, index) in items" :key="item.value" class="margintop radioChoose" id="radioChoose">
                <el-radio :label="index" v-model="radio">
                  <el-input type="text"  v-model="item.input" placeholder="【单选】"></el-input>
                    <el-radio  label="choose" v-model="item.isChoose">可填空</el-radio>
                    <el-button size="small" type="primary" class="delete" @click="deleteChoose(index)">删除</el-button>
                </el-radio>
              
            </div>

            <el-button size="small" type="primary" class="margintop addchoose" @click="addChoose">增加选项</el-button>
          </div>
          
          <div class="edit-wrap margintop">
            <div class="cancle" @click="showwrap=!showwrap">取消编辑</div><div class="finish" @click="finshEdit">完成编辑</div>
          </div>

       </div>
      </el-card>

     <!-- 提问编辑完成区域-->
     <el-card class="margintop question-wrap" v-show="radioQuestion" ref="questionWrap">
        <div class="btn-area">
          <el-button size="small" type="primary">上移</el-button>
          <el-button size="small" type="primary">下移</el-button>
          <el-button size="small" type="primary"  @click="showwrap=!showwrap">编辑</el-button>
          <el-button size="small" type="primary"  @click="removeChoose" >删除</el-button>
        </div>

       <!-- 单选编辑完成区域-->
       <div class="radioFinish" ref="radioFinish">
          <h4 ref="h4">{{question}}<span>【单选】</span></h4>
          <div v-for="item in items" :key="item.value">
            <el-radio>{{item.input}} <el-input  v-if="item.isChoose"></el-input></el-radio>
          </div>
       </div>

        <!-- 单选编辑区域 -->
       <div class="edit margintop" v-show="showwrap" ref="edit">
          <div class="question-area margintop">
            <el-input type="textarea" placeholder="请编辑问题？" v-model="question" ></el-input>
            <div v-for="(item, index) in items" :key="item.value" class="margintop radioChoose" id="radioChoose">
                <el-radio :label="index" v-model="radio">
                  <el-input type="text"  v-model="item.input" placeholder="【单选】"></el-input>
                    <el-radio  label="choose" v-model="item.isChoose">可填空</el-radio>
                    <el-button size="small" type="primary" class="delete" @click="deleteChoose(index)">删除</el-button>
                </el-radio>
              
            </div>

            <el-button size="small" type="primary" class="margintop addchoose" @click="addChoose">增加选项</el-button>
          </div>
          
          <div class="edit-wrap margintop">
            <div class="cancle" @click="showwrap=!showwrap">取消编辑</div><div class="finish" @click="finshEdit">完成编辑</div>
          </div>

       </div>
      </el-card>
    </div>
</template>

<script type="text/ecmascript-6">
export default {
  data() {
    return {
      options: [{
        value: '单选',
        label: '单选'
      },
      {
        value: '多选',
        label: '多选'
      },
      {
        value: '填空',
        label: '填空'
      }],
      radio: '1',
      radioQuestion: true,
      showwrap: true,
      question: '',
      items: [{
        'radio': '【单选】',
        'input': '【单选】',
        'isChoose': false
      },
      {
        'radio': '【单选2】',
        'input': '【单选】',
        'isChoose': false
      },
      {
        'radio': '【单选3】',
        'input': '【单选】',
        'isChoose': false
      }],
      newItem: {
        'radio': '【单选】',
        'input': '【单选】',
        'isChoose': false
      },
      value: ''
    }
  },
  methods: {
    // 增加选项
    addChoose() {
      this.items.push(this.newItem)
      this.newItem = { 'radio': '【单选】', 'input': '【单选】', 'isChoose': false } // 注意这个一定要重置
    },
    // 删除选项
    deleteChoose(index) {
      this.items.splice(index, 1)
    },
    // 完成编辑
    finshEdit(event) {
      var editWrap = this.$refs.edit
      // var s = this.$refs.radioFinish
      console.log($(".edit"))
      // $('.radioFinish').empty()
      // $('.radioFinish').append($(".question-area").clone())
      // $('.radioFinish .addchoose').hide();
      // $('.edit').hide()
    },
    // 删除编辑区域
    removeChoose() {
      console.log(this);
      $(event.target).parents('.question-wrap').hide();
    }
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

</style>