<template>
  <div class="breadcrumb">
    <el-breadcrumb separator="/">
      <el-breadcrumb-item :to="{ path: item.src }" 
      v-for="(item,index) in routeInfo" 
      :key="index">
      {{item.title}}
      </el-breadcrumb-item>
    </el-breadcrumb>
  </div>
</template>

<script>
export default {
  computed: {
    // 监听路由的变化，生成一个数组用于渲染面包屑信息
    routeInfo: function() {
      const matched = this.$route.matched;
      // 重新生成一个循环的数据格式
      const newArr = matched.map(v => {
        return {
          src: v.path,
          title: v.meta
        }
      })
      return newArr;
    }
  }
};
</script>

<style>
.breadcrumb{
    padding-bottom: 20px;
    border-bottom: 1px solid #ccc;
    margin-bottom: 20px;
}
</style>
