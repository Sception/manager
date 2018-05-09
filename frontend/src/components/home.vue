<template>
  <div class="home">
    <el-row>
      <el-table :data="bookList" stripe v-if="bookList" style="width: 100%" border>
        <el-table-column prop="id" label="编号"><template slot-scope="scope">{{scope.row.pk}}</template></el-table-column>
        <el-table-column prop="book_name" label="书名"><template slot-scope="scope">{{scope.row.fields.book_name}}</template></el-table-column>
        <el-table-column prop="add_time" label="添加时间"><template slot-scope="scope">{{scope.row.fields.add_time}}</template></el-table-column>
      </el-table>
    </el-row>
  </div>
</template>

<script>
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
      initBook(){
        var url = this.baseUrl + 'show_books';
        this.$api.get(url).then(response => {
          console.log(response);
          this.bookList = response.data.list;
        })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
