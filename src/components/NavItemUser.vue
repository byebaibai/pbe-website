<template>
  <b-nav-item-dropdown right class="rounded-white-background">
    <!-- Using 'button-content' slot -->
    <template #button-content>
      <b-avatar variant="info" src="https://placekitten.com/30/30"></b-avatar>
      <span class="nav-word">HelloWorld</span>
    </template>
    <b-dropdown-item href="#">我的主页</b-dropdown-item>
    <b-dropdown-item href="#">退出登录</b-dropdown-item>
  </b-nav-item-dropdown>
</template>

<script>
export default {
  name: "NavItemUser",
  data() {
    return {
      mainProps: { blank: true, width: 20, height: 20, class: 'm1' }
    }
  }
}
</script>

<style scoped>
.temp{
  height: 10px;
}
.rounded-white-background{
  background-color: white;
  border-radius: 999px;
}

.nav-word{
  color: darkgrey;
  margin-left: 10px;
  font-size: 10px;
}
</style>
