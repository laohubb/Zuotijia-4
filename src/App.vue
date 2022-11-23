
<template>
<!--  <router-link to="/">Home</router-link>-->
<div class="container">
  <div class="router">
    <router-link to="/topic1">promise改写</router-link>
    <router-link to="/topic2">垂直居中</router-link>
    <router-link to="/topic3">高度自适应</router-link>
    <router-link to="/topic4">表单组件</router-link>
    <router-link to="/topic5">topic5</router-link>
  </div>
</div>
<router-view></router-view>
</template>
<style scoped lang="scss">
.container{
  margin-top: 100px;
  display: flex;
  justify-content: center;
}
.router{
  width: 50%;
  display: flex;
  justify-content: space-around;
  color: darken(lightblue,20%);
  font-size: 20px;
  a{
    border: 1px solid lightblue;
    border-radius: 5px;
    padding: 5px;
  }
}
</style>

