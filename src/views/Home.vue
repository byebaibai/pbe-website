<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <StartButton />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
// import FlipCard from "../components/FlipCard";
import StartButton from "../components/StartButton";
export default {
  name: 'Home',
  components: {
    StartButton
  }
}
</script>
