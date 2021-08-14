<template>

  <b-container fluid>
    <div ref="flipbook">
      <flipbook class="flipbook" :pages="page_urls" :zooms="zooms" v-slot="flipbook" >
        <b-icon-chevron-compact-left font-scale="6" class="position-absolute ml-5"
                                     @click="flipbook.flipLeft" v-bind:style="leftArrow">
        </b-icon-chevron-compact-left>
        <b-icon-chevron-compact-right font-scale="6" class="position-absolute  mr-5"
                                      @click="flipbook.flipRight" v-bind:style="rightArrow">
        </b-icon-chevron-compact-right>
        <b-icon-blank font-scale="5" class="position-absolute blank-test" ></b-icon-blank>
      </flipbook>
    </div>

  </b-container>

</template>

<script>
import Flipbook from 'ytsj-flipbook-vue'
import { BIconChevronCompactLeft, BIconChevronCompactRight, BIconBlank} from 'bootstrap-vue'
// import Vue from 'vue'
export default {
  name: "FlipCard",
  components: {
    Flipbook,
    BIconChevronCompactLeft,
    BIconChevronCompactRight,
    BIconBlank
  },
  computed:{

  },
  data(){
    return{
      rightArrow:{
        zIndex: 1000
      },
      leftArrow: {
        zIndex: 1000
      },
      zooms: [1],
      page_urls:[
        "https://picsum.photos/400/600/?image=0",
        "https://picsum.photos/400/600/?image=1",
        "https://picsum.photos/400/600/?image=2",
        "https://picsum.photos/400/600/?image=3",
        "https://picsum.photos/400/600/?image=4",
        "https://picsum.photos/400/600/?image=5",
        "https://picsum.photos/400/600/?image=6",
        "https://picsum.photos/400/600/?image=7",
        "https://picsum.photos/400/600/?image=8"
      ],
      book_shape:{
        height: 600,
        width: 400
      }
    }
  },
  mounted () {
    this.matchArrowPos();
  },
  methods:{
    show(e){
      console.log(e.pageX, e.pageY, e.positionX, e.positionY);
    },
    matchArrowPos () {
      let top = "50%";
      let dist = "calc(50% + " + this.book_shape.width + "px)"
      this.$set(this.leftArrow, "top", top);
      this.$set(this.rightArrow, "top", top);
      this.$set(this.leftArrow, "right", dist);
      this.$set(this.rightArrow, "left", dist);
    }
  }

}
</script>

<style scoped>
.flipbook {
  width: 90vw;
  height: 90vh;
  margin: 0 auto;
}
.blank-test {
  background-color: blue;
  z-index: 999;
  right: calc(50% + 400px);
  top: calc(50% + 300px);
}
.left-arrow, .right-arrow{
  top: calc(50%);
  background-color: red;
  z-index: 999;
}
.left-arrow{
  right: calc(50% + 400px);
}
.right-arrow{
  left: calc(50% + 400px);;
}
</style>
