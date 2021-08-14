<template>
  <div class="container-bg">
    <div class="container">
      <div class="pt-3">
        <b-row>
          <b-col cols="5">
            <span class="sub-title float-left ml-1">基础信息</span>
          </b-col>
          <b-col >
            <span class="sub-title float-left">客观题得分</span>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="5">
            <div class="rounded-container shadow-sm text-left">
              <p class="pt-4 ml-3 mb-2">测评题目：{{question_name}}</p>
              <p class="pt-3 ml-3 mb-2">绘本名称：{{book_name}}</p>
              <p class="pt-3 ml-3 pb-2">答题者年龄：{{child_age}}岁</p>
            </div>
          </b-col>
          <b-col>
            <div class="rounded-container shadow-sm">
              <p class="pt-4 ml-4 mb-2 text-left" id="overall-score">
                {{object_score.overall}}<span id="overall-score-unit">分</span>
              </p>
              <p class="pt3 ml-4 mb-2 text-left" v-for="(dim_score, index) in object_score.dims" :key='index'>
                维度{{chinese_word[index]}}：{{dim_score}}分
              </p>
              <p class="position-absolute mt-4 pt-3 mr-5" id="time-cost">
                答题时长：{{object_score.time_cost}}分钟
              </p>
              <b-button class="position-absolute mb-4 mr-5 basic-btn" id="check-answer">查看答案</b-button>
            </div>
          </b-col>
        </b-row>
      </div>

      <div>
        <b-row>
          <span class="sub-title float-left ml-3">主观题答案</span>
        </b-row>

        <div class="rounded-container subject_questions shadow-sm" style="height: fit-content;" v-for="(answer, index) in subject_questions" :key="index">
          <p class="text-left question-intro ml-3 mr-3 pt-2" >
            {{fix(index+1, 2)}}.{{answer.name}}
            <b-button pill class="basic-btn page-btn ml-1">P{{fix(answer.page_num, 2)}}</b-button>
          </p>
          <p class="text-left ml-3 mr-3" style="font-weight: bolder">
            答案：{{answer.answer}}
            <b-icon-volume-up-fill font-scale="1" @click="playAudio(answer.audio_url)" role="button">
            </b-icon-volume-up-fill>
          </p>

        </div>
      </div>

      <div class="float-right">
        <b-button class="submit-btn" size="lg" variant="primary" v-b-modal.modal-prevent-closing>
          <b-icon-pencil-square class="mr-2"></b-icon-pencil-square>评分
        </b-button>

        <b-modal
            id="modal-prevent-closing"
            ref="modal"
            title="用户评分"
            @show="resetModal"
            @hidden="resetModal"
            hide-footer
        >
          <form ref="form" @submit.stop.prevent="handleSubmit">
            <div>
              <label>总评分：</label>
              <b-form-rating id="rating-inline" v-model="feedback.rate" no-border  value="1" stars="10" required></b-form-rating>
            </div>
            <div>
              <label>评价：</label>
              <b-form-textarea
                  id="textarea"
                  v-model="feedback.text"
                  placeholder="Enter something..."
                  rows="10"
                  max-rows="10"
                  required
                  :state="feedbackState"
              ></b-form-textarea>
              <b-form-invalid-feedback id="text-live-feedback">
                请输入对该学生主观题的评价
              </b-form-invalid-feedback>
            </div>
            <div class="text-right">
              <b-button pill class="mt-3" variant="primary" @click="comfirmSubmit" style="font-weight: bolder">提交</b-button>
            </div>
          </form>
        </b-modal>
      </div>
    </div>
  </div>
</template>

<script>
import { BIconVolumeUpFill, BIconPencilSquare} from 'bootstrap-vue'
export default {
  name: "RatingPage",
  components:{
    BIconVolumeUpFill,
    BIconPencilSquare
  },
  data(){
    return{
      question_name: "批判性思维测评",
      book_name: "我的情绪小怪兽",
      child_age: 12,
      chinese_word: ['一', '二', '三', '四'],
      object_score:{
        overall: 68,
        dims:[78,78,78,78],
        time_cost: 60
      },
      subject_questions:[
        {
          name: "这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍",
          answer: "这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍",
          page_num: 1,
          audio_url: "#"
        },
        {
          name: "这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍",
          answer: "这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍",
          page_num: 2,
          audio_url: "#"
        },
        {
          name: "这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍",
          answer: "这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍",
          page_num: 3,
          audio_url: "#"
        }
      ],
      feedback:{
        rate:1,
        text:''
      },
      name: '',
      feedbackState: null,
      submittedNames: []
    }
  },

  methods:{
    fix(num, length) {
      return ('' + num).length < length ? ((new Array(length + 1)).join('0') + num).slice(-length) : '' + num;
    },
    // TODO
    playAudio(url){
      console.log(url);
    },
    comfirmSubmit(bvModalEvt) {
      // Prevent modal from closing
      bvModalEvt.preventDefault();
      if (!this.checkFormValidity()) {
        return;
      }
      this.$bvModal.msgBoxConfirm('提交后的结果将直接发送给用户', {
        title: '确认提交',
        size: 'sm',
        buttonSize: 'sm',
        okVariant: 'primary',
        okTitle: '确认提交?',
        cancelTitle: '取消',
        footerClass: 'p-2',
        hideHeaderClose: false,
        centered: true
      })
          .then(value => {
            if(value){
              this.handleSubmit();
            }
          })
          .catch(err => {
            console.log(err);
          })
    },
    checkFormValidity() {
      const valid = (this.feedback.text.length > 0);
      this.feedbackState = !valid ? false : null;
      return valid
    },
    resetModal() {
      this.feedback.rate = 1
      this.feedback.text = ''
      this.feedbackState = null
    },
    handleSubmit() {
      // TODO
      // Push the name to submitted names
      this.submittedNames.push(this.name)
      // Hide the modal manually
      this.$nextTick(() => {
        this.$bvModal.hide('modal-prevent-closing')
      })
    }
  },
}
</script>

<style scoped>
.container{
  background: rgb(245,245,245);
}
#overall-score{
  font-size: 45px;
  font-weight: bold;
}
#overall-score-unit{
  font-size: 30px;
}
#time-cost{
  right: 0;
  top: 0;
}
#check-answer{
  right: 0;
  bottom: 0;
  border-radius: 10px;
}
.submit-btn{
  font-weight: bolder;
  border-width: 0;
  border-radius: 15px;
}
.page-btn{
  font-size: 12px;
}
.question-intro{
  font-size: medium;
}
.subject_questions{
  margin-bottom: 20px;
}
.rounded-container{
  position: relative;
  border-radius: 15px;
  background: white;
  max-width: 100%;
  height: 250px;
}
</style>
