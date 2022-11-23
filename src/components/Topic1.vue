<script setup>
import {request} from "../request/index.js";
import {onMounted} from "vue";

onMounted(async () => {
    const res = await request("/api/topic1");
    console.log(res);
});

</script>

<template>
  <div>题目1</div>

</template>
