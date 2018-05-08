<template>
  <div class="home">
    <el-row>
      <el-col :span="4">
        <el-input  placeholder="请输入输入书名"></el-input>
      </el-col>
      <el-button type="primary" class="add_button">添加</el-button>
    </el-row>
    <el-row>
      <!--<el-table :data="bookList" style="width: 100%" border>-->
        <!--<el-table-column prop="id" label="编号" min-width="180"><template scope="scope">{{}}</template></el-table-column>-->
        <!--<el-table-column prop="name" label="姓名" width="180"></el-table-column>-->
        <!--<el-table-column prop="address" label="地址"></el-table-column>-->
      <!--</el-table>-->
    </el-row>

  </div>
</template>

<script>
  const prefix = 'http://127.0.0.1:8000/api/';
  export default {
    name: 'home',
    data() {
      return {
        bookList:''
      }
    },
    created(){
      this.initBook();
    },
    methods:{
      initBook:() => {
        var url = prefix + 'show_books';
        this.$api.get(url).then(response => {
          console.log(response);
        })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .home .add_button {
    float: left;
  }
</style>
