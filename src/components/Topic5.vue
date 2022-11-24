<script setup>
import CustomPassword from './CustomPassword.vue'
import {ref} from "vue";
const password=ref()

</script>

<template>
<div class="container">
  <CustomPassword v-model:password="password" :len="6"></CustomPassword>
  <div>当前密码是{{password}}</div>
</div>
</template>

<style scoped lang="scss">
.container{
  align-items: center;
  display: flex;
  flex-direction: column;
}
</style>
