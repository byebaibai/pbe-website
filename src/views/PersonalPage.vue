<template class="container-bg">
  <div class="container-bg">
    <div class="container" >
      <b-row align-v="stretch" id="personal-page">
        <b-col cols="3">
          <b-img fluid src="https://placekitten.com/300/300" alt="Image 1"></b-img>
        </b-col>
        <b-col cols="9">
          <b-row align-h="between">
            <b-col cols="1">
              <span class="personal-name">HelloWorld</span>
            </b-col>
            <b-col cols="4">
              <b-link href="#" style="text-decoration:underline">补充资料</b-link>
            </b-col>
          </b-row>
          <hr/>
          <div class="text-left">
            <p>
              电话：{{user_info.tel}}
            </p>
            <p>
              年龄：{{user_info.age}}岁
            </p>
            <p>
              学龄：{{user_info.school_age}}
            </p>
            <span class="prefer-tags">
              偏好标签：
              <b-badge v-for="(t, index) in user_info.tags" :key='index' pill variant="secondary" class="prefer-tag">{{t}}</b-badge>
            </span>
          </div>
        </b-col>
      </b-row>

      <div>
        <b-row>
          <span class="sub-title ml-3">评测记录</span>
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
          <span class="sub-title ml-3">阅读记录</span>
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
  name: "PersonalPage",
  components: {
    BookCard
  },
  data() {
    return {
      tags:['天文', '恐龙', '科学'],
      user_info:{
        'tel':18810313655,
        'age':12,
        'school_age':'⼩学六年级',
        'tags':['天文', '恐龙', '科学']
      }
    }
  }

}
</script>

<style scoped>

.personal-name{
  font-weight: bold;
  font-size: x-large;
}
#personal-page{
  padding-top: 30px;

}
.prefer-tags{
  display: flex;
  align-items: center;
  justify-content: left;
}
.prefer-tag{
  margin-right: 6px;
}

</style>
