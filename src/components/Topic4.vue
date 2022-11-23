<script setup>
import {reactive, ref} from "vue";
//自定义主题色
const themeColor= ref('#81ccad');
const stepNow = ref(1);
const steps = reactive(
    {
      step1: {
        title: '➊ 请填写用户名',
      },
      step2: {
        title: '➋ 请填写手机号',
      },
      step3: {
        title: '➌ 请填写密码',
      },
    }
);
const form = reactive(
    {
      step1Label: '用户名',
      step1Holder: '请输入用户名',
      step1Content: '',
      step2Label: '手机号',
      step2Holder: '请输入手机号',
      step2Content: '',
      step3Label: '密码',
      step3Holder: '请输入密码',
      step3Content: '',

    }
)
const buttonTheme1=reactive({borderColor: themeColor.value,color: themeColor.value})
const buttonTheme2=reactive({borderColor: themeColor.value,backgroundColor:themeColor.value,color: 'white'})
const changeStep = (number) => {
  stepNow.value = number;
}
const nextStep = () => {
  if(stepNow.value < 3){
    stepNow.value++;
  }
}
const preStep = () => {
  if(stepNow.value > 1){
    stepNow.value--;
  }
}

const submit = () => {
  if(form.step1Content && form.step2Content && form.step3Content){
    alert(`${form.step1Label}：${form.step1Content}，${form.step2Label}：${form.step2Content}，${form.step3Label}：${form.step3Content}`)
  }else{
    alert('请填写完整信息')
  }

}

const reset=()=>{
  form.step1Content='';
  form.step2Content='';
  form.step3Content='';
  changeStep(1)
}
</script>

<template>
  <div class="container">
   <div class="box">
     <div class="head">
       <div class="step" :class="[stepNow===1&&'active']" @click="changeStep(1)">{{ steps.step1.title }}</div>
       <div class="step" :class="[stepNow===2&&'active']" @click="changeStep(2)">{{ steps.step2.title }}</div>
       <div class="step" :class="[stepNow===3&&'active']" @click="changeStep(3)">{{ steps.step3.title }}</div>

     </div>
     <div class="content">
       <div class="box" v-if="stepNow===1">
         <div>{{ form.step1Label }}</div>
         <input :placeholder="form.step1Holder" v-model="form.step1Content">

       </div>
       <div class="box" v-if="stepNow===2">
         <div>{{ form.step2Label }}</div>
         <input :placeholder="form.step2Holder"  v-model="form.step2Content">

       </div>
       <div class="box" v-if="stepNow===3">
         <div>{{ form.step3Label }}</div>
         <input :placeholder="form.step3Holder"  v-model="form.step3Content">
       </div>
     </div>

     <div class="buttons">
       <button class="bt1" @click="reset">重 置</button>
       <button @click="preStep" class="bt2" :style="buttonTheme1">上一步</button>
       <button v-if="stepNow!=3" @click="nextStep" class="bt3" :style="buttonTheme2">下一步</button>
       <button v-else @click="submit" class="bt3" :style="buttonTheme2"  >提交</button>

     </div>
   </div>
  </div>
</template>
<style scoped lang="scss">
.container {

  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.head {
  cursor: pointer;
  display: flex;
  .step{
    padding: 10px 35px;
    background-color: #f2f4f8;
    &.active {
      background-color: #81ccad;
      color: white;
    }
  }

}

.content {
  margin-top: 20px;
  .box {
    display: flex;
    align-items: center;
    justify-content: space-between;
    input {
      &:focus{
        outline: none;
      }
      padding: 4px 14px;
      border: 1px solid gainsboro;
      border-radius: 2px;
      width: 400px;
    }
  }

}

.buttons{
  display: flex;
  justify-content: right;

  width:100%;
  margin-top: 30px;
  button{
    margin-left: 12px;
    cursor: pointer;
    background-color: white;
    border: 1px solid lightgray;
    border-radius: 2px;
    padding: 5px 10px;
    font-size: 10px;
  }


}
</style>
