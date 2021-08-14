<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      <b-navbar-brand>
        {{ this.Constants.COMMPANY_NAME }}
        <img src="https://placekitten.com/g/30/30" class="d-inline-block align-top" alt="Kitten">
      </b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
<!--        <b-navbar-nav>-->
<!--          <b-nav-item href="#">Link</b-nav-item>-->
<!--          <b-nav-item href="#" disabled>Disabled-->
<!--          </b-nav-item>-->
<!--        </b-navbar-nav>-->

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" placeholder="绘本、测评"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">搜索</b-button>
          </b-nav-form>

          <NavItemUser fluid style="margin-left: 30px;"/>

        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
import NavItemUser from "@/components/NavItemUser";
export default {
  name: "nav",
  components:{
    NavItemUser,
  },

}
</script>

<style scoped>
.temp{
  height: 10%;
  width: auto;
}
</style>
