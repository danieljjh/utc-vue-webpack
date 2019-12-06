<template>
  <div class="home">
    <div class="pagetitle">技师列表</div>
    <el-row class="choose">
      <el-button
        type="primary"
        @click="createstaff() "
        class="add"
      >添加</el-button>
    </el-row>
    <el-table
      v-bind:data="tableData"
      border
      style="width: 100%"
    >
      <el-table-column
        prop="user_name"
        label="用户名"
      ></el-table-column>
      <el-table-column
        prop="user_tel"
        label="用户电话"
      ></el-table-column>
      <el-table-column
        prop="uid"
        label="工作ID"
      ></el-table-column>
      <el-table-column
        prop="worker_type"
        label="工作类型"
      ></el-table-column>
      <el-table-column
        prop="reg_time"
        label="注册时间"
      ></el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: "",
      tableData: null
    };
  },
  mounted() {
    let _that = this;
    // console.log("work", this.$api);

    _that.$axios
      .post(_that.$api + "/api/dis/getworklist", {
        city: "上海市"
      })
      .then(res => {
        if (res.data == "") {
          _that.$message("请正确输入城市或该城市没有员工");
        } else {
          _that._data.tableData = res.data;
        }
      });
  },
  methods: {
    createstaff: function() {}
  }
};
</script>
<style>
.choose {
  margin: 10px 0;
}
.choosetitle {
  width: 20%;
  display: inline-block;
}
.chooseinp {
  width: 60%;
  display: inline-block;
}
.add {
  float: right;
  margin: 5px 47px 15px 0;
}
</style>
