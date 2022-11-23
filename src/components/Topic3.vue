<script setup>

</script>

<template>
  <div>
    自适应最高高度
    <div class="container">
      <div class="box-1">模块1</div>
      <div class="box-2">模块2</div>
      <div class="box-3">模块3</div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.container{
  margin: 0 auto;
  justify-content: center;
  width: 600px;
  display: flex;
  background-color:#f2f2f2 ;
}
.box-1{
  width: 120px;
  background-color: pink;
}
.box-2{
  width: 120px;
  background-color: #71bff6;
}
.box-3{
  width: 120px;
  height: 150px;
  background-color: #305376;
}
</style>
