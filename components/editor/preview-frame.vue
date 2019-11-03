<template>
  <div class="preview_wrap">
    <div class="preview_con">
      <div class="preview_head">
        <h1 class="tit">Preview</h1>
      </div>
      <div class="preview_body">
        <!--여기에 구성요소 추가-->
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    name: "preview-frame"
  }
</script>

<style scoped>
  .preview_wrap {
    width: 396px;
    height: 726px;
    margin-left: 20px;
    border: 2px solid #dadada;
    padding: 0 12px;
    border-radius: 35px;
    background-color: #ebebeb;
  }
  .preview_head{
    height: 68px;
    padding: 20px 0;
  }
  .preview_head .tit {
    text-align: center;
  }
  .preview_body{
    background-color: #fff;
    height: 617px;
    border: 2px solid #ddd;
  }
</style>
