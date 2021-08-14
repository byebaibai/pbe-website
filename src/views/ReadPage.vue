<template>
  <div class="container-bg">
    <FlipCard />
<!--    <div class="container">-->
<!--      <div class="ml-5 mr-5">-->
<!--        <b-img-lazy :src="book.prev_img_url" fluid-grow alt="preview image" class="mt-5 mb-3"></b-img-lazy>-->
<!--        <h3>{{book.title}}</h3>-->
<!--        <p>{{book.explanation}}</p>-->
<!--        <b-button class="basic-btn" @click="showMsgBoxTwo">阅读绘本</b-button>-->
<!--      </div>-->
<!--    </div>-->
  </div>
</template>

<script>
import FlipCard from "../components/FlipCard";
export default {
  name: "ReadPage",
  components:{
    FlipCard
  },
  data(){
    return{
      book:{
        id: 1,
        title: '我的情绪小怪兽',
        explanation: '这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍这是一段题目介绍',
        prev_img_url: 'https://picsum.photos/300/150/?image=41'
      }
    }
  },
  methods: {
    showMsgBoxTwo() {
      this.boxTwo = ''
      this.$bvModal.msgBoxConfirm('该绘本有⼀套测评题⽬《批判性思维测评》，建议⾸次阅读时进⾏测评哦，是否要边读边进⾏测评？', {
        title: 'd',
        buttonSize: 'sm',
        okVariant: 'primary',
        okTitle: '去测评',
        cancelTitle: '直接阅读',
        headerClass: 'p text-center border-bottom-0',
        footerClass: 'border-top-0',
        hideHeaderClose: false,
        centered: true
      })
          .then(value => {
            console.log(value);
          })
          .catch(err => {
            console.log(err);
          })
    }
  }
}
</script>

<style scoped>

</style>
