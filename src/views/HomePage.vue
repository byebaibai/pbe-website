<template>
  <div class="container-bg">
    <div class="container p-0" >
      <b-carousel
          id="carousel-1"
          v-model="slide"
          :interval="4000"
          controls
          indicators
          background="#ababab"
          img-width="1024"
          img-height="480"
          style="text-shadow: 1px 1px 2px #333;"
          @sliding-start="onSlideStart"
          @sliding-end="onSlideEnd"

      >
        <b-carousel-slide v-for="(item, index) in slides" :key='index' :img-src=item.img>
        </b-carousel-slide>
      </b-carousel>
    </div>
    <div class="container" >
      <div>
        <b-row>
          <span class="sub-title ml-3">测评题目</span>
        </b-row>
        <b-row class="flex-nowrap overflow-auto mr-1">
          <BookCard />
          <BookCard />
          <BookCard />
          <BookCard />
        </b-row>
      </div>

      <div>
        <b-row>
          <span class="sub-title ml-3">绘本阅读</span>
        </b-row>
        <b-row class="flex-nowrap overflow-auto mr-1">
          <BookCard />
          <BookCard />
          <BookCard />
          <BookCard />
        </b-row>
      </div>
    </div>
  </div>
</template>

<script>
import BookCard from "../components/BookCard";

export default {
  name: "HomePage",
  components: {
    BookCard
  },
  data() {
    return {
      slide: 0,
      sliding: null,
      slides:[
        {
          'img':'https://picsum.photos/1024/480/?image=54'
        },
        {
          'img':'https://picsum.photos/1024/480/?image=52'
        },
        {
          'img':'https://picsum.photos/1024/480/?image=58'
        }
      ]
    }
  },
  methods: {
    onSlideStart() {
      this.sliding = true
    },
    onSlideEnd() {
      this.sliding = false
    }
  }
}
</script>

<style scoped>

</style>
