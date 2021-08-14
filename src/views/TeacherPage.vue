<template>
  <div class="container-bg">
    <div class="container">
      <div>
        <b-row>
          <span class="sub-title ml-3">测评记录</span>
        </b-row>
        <b-row class="text-right">
          <div class="ml-auto mr-3 mb-2">
            <b-button variant="outline-danger"  size="sm"
                      :disabled="(typeof(this.$refs.vuetable) === 'undefined') ? true :
                      (this.$refs.vuetable.selectedTo.length === 0)">删除</b-button>
          </div>
        </b-row>
        <vuetable ref="vuetable"
                  :fields=fields
                  :api-mode="false"
                  :data=table_data
        ></vuetable>

      </div>
    </div>
  </div>
</template>

<script>
import Vuetable from 'vuetable-2'
import VuetableFieldCheckbox from 'vuetable-2/src/components/VuetableFieldCheckbox.vue';

export default {
  name: "TeacherPage",
  components: {
    Vuetable
  },
  // this.$refs.vuetable.selectedTo
  data() {
    return {
      deleteBtnStatus: true,
      fields:[
        {
          "name":VuetableFieldCheckbox,
          "titleClass": 'center aligned',
          "dataClass": 'center aligned',

        },
        {
          "name":"id",
          "title":"编号"
        },
        {
          "name":"question_name",
          "title":"题目名称"
        },
        {
          "name":"related_book",
          "title":"关联绘本"
        },
        {
          "name":"child_age",
          "title":"儿童年龄"
        },
        {
          "name":"status",
          "title":"评价状态",
           formatter: (value) => (value === true) ? "已评价" : "未评价"
        },
        {
          "name":"operation",
          "title":"操作"
        },

      ],
      table_data:[
        {"id":1, "question_name":2, "related_book":3, "child_age":4, "status":true, "operation":1},
        {"id":2, "question_name":2, "related_book":3, "child_age":4, "status":false, "operation":1},
        {"id":3, "question_name":2, "related_book":3, "child_age":4, "status":true, "operation":1},
        {"id":4, "question_name":2, "related_book":3, "child_age":4, "status":false, "operation":1},
        {"id":5, "question_name":2, "related_book":3, "child_age":4, "status":true, "operation":1},
      ]
    }
  },
  methods:{

  }

}
</script>

<style scoped>

</style>
