<template>
  <div class="editor-wrap">
    <header>
      <div class="cont-wrap">
        <div class="cont-tit">타이틀 타이틀 타이틀 타이틀</div>
        <div class="cont-url">http://urlname.i-on.net</div>
      </div>
    </header>
    <section>
      <component-bar></component-bar> <!--chloe-->
      <preview-frame></preview-frame> <!--mary-->
      <edit-frame></edit-frame> <!--daisy-->
    </section>
    <footer>
      <div class="btn-wrap">
        <a class="btn" @click="save">저장</a>
      </div>
    </footer>
  </div>
</template>

<script>
import ComponentBar from '~/components/editor/component-bar'
import PreviewFrame from '~/components/editor/preview-frame'
import EditFrame from '~/components/editor/edit-frame'
export default {
  components: {
    ComponentBar,
    PreviewFrame,
    EditFrame,
  },
  methods: {
    save() {
      alert('save test');
    }
  }
}
</script>

<style scoped>
  .editor-wrap * {
    /*border: 1px solid black;*/
  }
  /*********** header ***********/
  header {
    height: 10vh;
    background-color: #303437;
    display: flex;
    align-items: center;
  }
  header > .cont-wrap {
    display: flex;
    margin-left: 15px;
  }
  header > .cont-wrap > div {
  }
  header > .cont-wrap > .cont-tit {
    color: white;
    font-size: 1.3rem;
  }
  header > .cont-wrap > .cont-url {
    color: #868686;
    margin-left: 15px;
  }

  /*********** section ***********/
  section {
    height: 80vh;
  }
  /*********** footer ***********/
  footer {
    height: 10vh;
    background-color: #e7e7e7;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  /*********** button ***********/
  .btn-wrap {
    width: 50vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .btn {
    width: 100px;
    height: 35px;
    text-align: center;
    line-height: 35px;
    border-radius: 30px;
    background-color: #94C2ED; /* 버튼색 임시 */
    color: white;
    font-size: 0.9rem;
    cursor:pointer;
    font-weight: bold;
  }

</style>

