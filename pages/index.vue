<template>
  <div class="editor-wrap">
    <header>
      <div class="cont-wrap">
        <div class="cont-tit">타이틀 타이틀 타이틀 타이틀</div>
        <div class="cont-url">http://urlname.i-on.net</div>
      </div>
    </header>
    <section>
      <!-- 페이지 추가 영역 -->
      <div class="page-view">
        <div v-show="isShowList">
          <div class="page-view-list"> <!-- 페이지 추가 리스트 -->
            <div class="page-view-col" v-for="(page,index) in pageList" v-bind:key="index">
              <span>{{ page.title }}</span>
              <button @click="removePage(index)">X</button>
            </div>
          </div>
          <div class="page-add-area"> <!-- 페이지 추가 버튼 -->
            <button @click="addPage">페이지 추가</button>
          </div>
        </div>
        <div class="page-view-toggle"> <!-- 보이기/숨기기 -->
          <button @click="listToggle">{{ toggleTitle }}</button>
        </div>
      </div>
      <!-- //페이지 추가 영역 -->
      <div class="edit-area">
        <component-bar></component-bar> <!--chloe-->
        <preview-frame></preview-frame> <!--mary-->
        <edit-frame></edit-frame> <!--daisy-->
      </div>
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
  data() {
    return {
      pageList: [
        { title: "홈" },
        { title: "메뉴" },
        { title: "게시판" },
        { title: "오시는길" }
      ],
      toggleTitle: "숨기기",
      isShowList: true
    }
  },
  methods: {
    save() {
      alert('save test');
    },
    addPage() { // 페이지 리스트 추가
      this.pageList.push({ title: "리스트추가["+this.pageList.length+"]" });
    },
    removePage(index) { // 페이지 리스트 삭제
      this.pageList.splice(index,1);
    },
    listToggle() { // 페이지 리스트 Show/Hide
      this.isShowList = !this.isShowList;
      this.toggleTitle = (this.isShowList ? "숨기기" : "보이기");
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
  section > .edit-area {
    display: flex;
    justify-content: space-between;
  }
  section > .page-view > div {
    display: flex;
  }
  section > .page-view > div > .page-view-list {
    width: 90%;
    height: 200px;
    display: flex;
    border: 1px solid black;
  }
  section > .page-view > div > .page-view-list > .page-view-col {
    border: 1px solid black;
    width: 130px;
  }
  section > .page-view > div > .page-add-area {
    border: 1px solid black;
    width: 10%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  section > .page-view > .page-view-toggle {
    border: 1px solid black;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  section > .page-view > .page-view-toggle > button {
    margin: 5px;
  }
  /*********** footer ***********/
  footer {
    width:100%;
    height: 10vh;
    background-color: #e7e7e7;
    display: flex;
    justify-content: center;
    position: fixed;
    bottom: 0;
  }

  /*********** button ***********/
  .btn-wrap {
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
