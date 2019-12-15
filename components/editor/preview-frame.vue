<template>
  <div class="preview_wrap">
    <div class="preview_con">
      <div class="preview_head">
        <h1 class="tit">Preview</h1>
      </div>
      <div class="preview_body">
        <!--텍스트-->
        <c-txt v-if="drawer" v-for="index in $store.state.counter" :key="index.id" ></c-txt>
        <!--이미지한장-->
<!--        <c-img></c-img>-->
        <!--텍스트이미지여러장-->
<!--        <c-txt-img-multi></c-txt-img-multi>-->
        <!--이미지여러장-->
<!--        <c-img-multi></c-img-multi>-->
        <!--지도-->
<!--        <c-map></c-map>-->
        <!--구분선-->
        <c-div-line></c-div-line>
      </div>
    </div>
  </div>
</template>
<script>
    import CDivLine from "./previewchild/cDivLine";
    import CImg from "./previewchild/cImg";
    import CImgMulti from "./previewchild/cImgMulti";
    import CMap from "./previewchild/cMap";
    import CTxt from "./previewchild/cTxt";
    import CTxtImgMulti from "./previewchild/cTxtImgMulti";

    export default {
        name: "preview-frame",
        components: {CTxtImgMulti, CTxt, CMap, CImgMulti, CImg, CDivLine},
        data() {
            return {drawer:false};
        },
        created() {
            this.$bus.$on('title1', () => {
                this.drawer = true;
            });
        }
    }
</script>

<style scoped>
  .preview_wrap {
    margin-right: auto; /*--20191215추가--*/
    margin-left: auto; /*--20191215추가--*/
    width: 396px;
    border: 2px solid #dadada;
    padding: 0 12px;
    border-radius: 35px;
    background-color: #ebebeb;
  }

  .preview_head {
    height: 68px;
    padding: 20px 0;
  }

  .preview_head .tit {
    text-align: center;
  }

  .preview_body {
    background-color: #fff;
    height: 617px;
    border: 2px solid #ddd;
  }

  .preview_con {
    height: 100%;
  }

  .preview_body {
    height: 80%;
  }

  ._component {
    position: relative;
    cursor: pointer;
  }

  ._component:after {
    display: none;
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    z-index: 1100;
    border: 2px dotted #00c73c;
    content: '';
  }
  ._component:hover:after {
    display: block;
    background-color: transparent;
  }
</style>
