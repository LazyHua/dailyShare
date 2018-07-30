<template>
  <div id="app">
    <img src="./assets/logo.png" @click="open">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: "App",
  provide: function() {
    return {
      parentMethod: this.parentMethod
    };
  },
  methods: {
    parentMethod() {
      alert("我是妈妈！");
    },
    open() {
      this.$confirm("此操作将永久删除该文件, 是否继续?", "提示", {
        confirmButtonText: "确定",
        cancelButtonText: "取消",
        type: "warning"
      })
        .then(() => {
          this.$message({
            type: "success",
            message: "删除成功!"
          });
        })
        .catch(() => {
          this.$message({
            type: "info",
            message: "已取消删除"
          });
        });
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
