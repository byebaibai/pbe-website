<template>
  <div class="home">
<!--    <img alt="Vue logo" src="../assets/logo.png">-->
    <FlipCard />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import FlipCard from "../components/FlipCard";
export default {
  name: 'Home',
  components: {
    FlipCard
  }
}
</script>
