<template>
  <div class="container-bg">
    <div class="container" >
<!--      <b-row>-->
<!--        <b-col>-->
<!--          <b-img fluid src="https://placekitten.com/200/200" alt="Image 1"></b-img>-->
<!--        </b-col>-->
<!--      </b-row>-->
      <b-row>
        <b-col class="footer-relate-link">
          <b-link class="ml-2 mr-2" v-for="(item, index) in relate_links"
                  :key="index" style="color: black;" :href=item.link>{{item.name}}</b-link>
        </b-col>

      </b-row>
      <b-row>
        <b-col>
          <span class="copyright-word">
            Copyright©2021  <b-link :href=homepage_url>{{this.Constants.COMMPANY_NAME}}</b-link> Powered by XXX
                    <b-link :href=icp_url>京ICP备XXXXXX号-X</b-link>
          </span>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      relate_links:[
        {'name':'联系我们','link':'#'},
        {'name':'加入我们','link':'#'},
        {'name':'意见反馈','link':'#'},
        {'name':'关于我们','link':'#'},
        {'name':'联系我们','link':'#'},
        {'name':'版权声明','link':'#'},
        {'name':'隐私保护','link':'#'},
        {'name':'商务合作','link':'#'},
      ],
      homepage_url: '#',
      icp_url: '#'
    }
  }
}
</script>

<style scoped>
.container-bg {
  background: rgb(245,245,245);
  padding-top: 100px;
  padding-bottom: 50px;
}
.container {
  background: rgb(245,245,245);
}
.footer-relate-link{
  margin-top: 10px;
  margin-bottom: 10px;
  font-size: small;
}
.copyright-word{
  margin-top: 10px;
  margin-bottom: 10px;
  font-size: small;
}
</style>
