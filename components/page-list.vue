<template>
  <div class="page-view">
    <div v-show="isShowList">
      <div class="page-view-list"> <!-- 페이지 추가 리스트 -->
        <div class="page-view-col" v-for="(page,index) in pageList" v-bind:key="index" @click="focusPage(index)">
          <editable-text :default="page.title"/>
          <p>{{page.title}}</p>
          <button @click="removePage(index)">X</button>
          <div>{{page.isFocus}}</div> <!-- focus test -->
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
</template>

<script>
import EditableText from '~/components/utils/editable-text'
  export default {
    name: "page-list",
    components: {
      EditableText
    },
    created() {
      this.pageListUpdate();
    },
    data() {
      return {
        pageList: [
          { title: "홈", isFocus:true },
          { title: "메뉴", isFocus:false },
          { title: "게시판", isFocus:false },
          { title: "오시는길", isFocus:false }
        ],
        toggleTitle: "숨기기",
        isShowList: true
      }
    },
    methods: {
      addPage() { // 페이지 리스트 추가
        this.pageList.push({ title: "리스트추가["+this.pageList.length+"]", isFocus:false });
      },
      removePage(index) { // 페이지 리스트 삭제
        console.log(index);
        this.pageList.splice(index,1);
      },
      listToggle() { // 페이지 리스트 Show/Hide
        this.isShowList = !this.isShowList;
        this.toggleTitle = (this.isShowList ? "숨기기" : "보이기");
      },
      pageListUpdate() {
        this.$emit("childPageList", this.pageList);
      },
      focusPage(index) {
        console.log(index);
        for(let i=0; i<this.pageList.length; i++) {
          if(i == index) this.pageList[i].isFocus = true;
          else this.pageList[i].isFocus = false;
        }
      }
    }
  }


</script>

<style scoped>
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
</style>
