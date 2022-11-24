<script setup>

</script>

<template>

  <div class="wrapper">
    <ul>
      <li>方案1:使用flex</li>
      <li>方案2:使用table表格,单元框内容会自动垂直居中</li>
      <li>方案3:子绝父相,父元素相对定位,子元素绝对定位,再通过transform: translate移动一半的宽高实现居中</li>
    </ul>

    <div class="container">

      <div class="box-1">
        <div>content</div>
      </div>

      <table class="box-2">
        <tr>
          <td>content</td>
        </tr>
      </table>

      <div class="box-3">
        <div class="content">content</div>
      </div>
    </div>

  </div>


</template>
<style lang="scss" scoped>
.wrapper{
  margin-top: 50px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
.container{
  display: flex;
  [class^="box-"] {
    border: 1px solid #000;
    height: 200px;
    width: 200px;
  }

  .box-1 {
    border: 1px solid black;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .box-2{
    text-align: center;
  }
  .box-3 {
    position: relative;
    .content{
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }
}


</style>
