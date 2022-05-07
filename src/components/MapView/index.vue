<template>
<div class="map-view">
  <el-card>
    <div class="button-in">
      <el-button type="info" @click="toOtherView" plain>外卖销售数据大盘</el-button>
    </div>
  </el-card>
</div>
  
</template>

<script>
  export default {
    methods: {
      toOtherView (){
        this.$router.replace('/bmap')
      }
    },
  }
</script>

<style lang="scss" scoped>
.map-view{
  display: flex;
  margin-top: 20px;
  justify-content: center;
  .el-button{
    padding: 20px;
  }
  .button-in{
    padding: 10px 100px;
  }
}
</style>