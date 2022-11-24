<script setup>
import {request} from "../request/index.js";
import {onMounted} from "vue";

onMounted(async () => {
    const res = await request("/api/topic1");
    console.log(res);
});

</script>

<template>
  <div class="container">
    <div>promise改写,见代码</div>
  </div>

</template>
<style>
.container{
  display: flex;
}
</style>
