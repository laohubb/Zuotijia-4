<script setup>
import {ref} from "vue";

const props = defineProps(['len', 'password'])
defineEmits(['update:password'])

const len = props.len
const pwdList = ref([]);

const ipt = ref()


const keyUp = (ev, index, emit) => {

  let indexNow = index

  if (/[0-9]/.test(ev.key)) {
    indexNow += 1
    pwdList.value[index] = ev.key;
    if (pwdList.value.length < 6) {
      ipt.value[indexNow].focus()
    }
  }
  if (ev.key === 'Backspace') {
    pwdList.value.pop()
    click()
  }
  emit('update:password', pwdList.value.join(""))
}

const click = () => {
  const maxLen = pwdList.value.length
  if (maxLen < 6) {
    ipt.value[maxLen].focus()
  } else if (maxLen === 6) {
    ipt.value[maxLen - 1].focus()
  }

}
</script>

<template>
  <div class="container">
    <div class="box">
      <input type="password" ref="ipt" @click="click" maxlength="1"
             @keyup.prevent="keyUp($event,i,$emit)" @keydown.prevent
             v-model="pwdList[i]" v-for="(v,i) in len" :key="i">

    </div>


  </div>
</template>

<style scoped lang="scss">
.container {
  display: flex;
  justify-content: center;
}

.box {
  display: flex;

  input {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    width: (230px/6);

    &:focus {
      outline: none;
    }
  ;
    border-top: 3px solid #989898;
    border-left: 3px solid #989898;
    border-right: 1px solid rgb(238, 238, 238);
    border-bottom: 3px solid rgb(238, 238, 238);
  }
}


</style>
