<template>
  <div class="ml-3 mr-3 book-card ">
    <b-img src="https://placekitten.com/300/300" alt="Left image" class="book-card-bg"></b-img>
    <span class="book-age">5-6岁</span>
    <span class="book-title">我的情绪小怪兽</span>
    <span class="book-history">读到5/15，点击继续</span>
    <span class="book-tag border">已读</span>
  </div>
</template>

<script>
export default {
  name: "BookCard"
}
</script>

<style scoped>
.book-card{
  position: relative;
  scroll-margin-right: 15px;
}
.book-card-bg{
  /*max-width: 100%;*/
  width: 275px;
  height: 175px;
  object-fit: none;
}
.book-age{
  position: absolute;
  bottom: 7px;
  right: 10px;
  color: white;
  font-size: medium;
}
.book-title{
  position: absolute;
  bottom: 7px;
  left: 10px;
  color: white;
  font-size: medium;
}
.book-history{
  position: absolute;
  top: 7px;
  left: 10px;
  color: white;
  font-size: medium;
  text-decoration: underline;
}
.book-tag{
  position: absolute;
  top: 7px;
  right: 10px;
  color: white;
  font-size: small;
}
</style>
