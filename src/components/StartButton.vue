<template>
  <a href="javascript:;" class="shadow">
    <img :src="button_url" alt="" style = "width:130px; height: 100px; "
         @mousedown="button_url = image_down_url"
         @mouseup="button_url = image_up_url">
  </a>
</template>

<script>
export default {
  name: "StartButton",
  data(){
    return {
      image_down_url: 'https://picsum.photos/400/600/?image=0',
      image_up_url: 'https://picsum.photos/400/600/?image=4',
      button_url: 'https://picsum.photos/400/600/?image=0'
    }
  }
}
</script>

<style scoped>
.shadow {
  display: inline-block;
  width: 130px;
  height: 100px;
}

.shadow :hover {
  filter: drop-shadow(7px 7px 5px #868686);
  width: 130px;
  height: 100px;
}
</style>
