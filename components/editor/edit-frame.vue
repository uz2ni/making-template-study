<template>
  <!-- Component Detail Setting -->
  <div class="edit-frame">
    <!-- 타이틀 텍스트 -->
    <template v-if="activeComp === 'comp1'">
      <div class="comp-tit">
        <p>타이틀 텍스트</p>
      </div>
      <article>
        <label><input type="radio" name="size" value="small"> 작게</label>
        <label><input type="radio" name="size" value="lazy" checked> 크게</label>
      </article>
      <article>
        <label><input type="radio" name="align" value="left"> 왼쪽 정렬</label>
        <label><input type="radio" name="align" value="center" checked> 가운데 정렬</label>
      </article>
      <article>
        <textarea placeholder="타이틀을 입력해주세요"></textarea>
      </article>
    </template>
    <!-- 본문형 텍스트 -->
    <template v-else-if="activeComp === 'comp2'">
      <div class="comp-tit">
        <p>텍스트</p>
      </div>
      <article>
        <label><input type="radio" name="textType" value="body" checked> 본문형</label>
        <label><input type="radio" name="textType" value="list"> 목록형</label>
      </article>
      <article>
        <label><input type="radio" name="align" value="left"> 왼쪽 정렬</label>
        <label><input type="radio" name="align" value="center" checked> 가운데 정렬</label>
      </article>
      <article>
        <textarea placeholder="내용을 입력해주세요"></textarea>
      </article>
    </template>
    <!-- 목록형 텍스트 -->
    <template v-else-if="activeComp === 'comp3'">
      <div class="comp-tit">
        <p>텍스트</p>
      </div>
      <article>
        <label><input type="radio" name="textType" value="body"> 본문형</label>
        <label><input type="radio" name="textType" value="list" checked> 목록형</label>
      </article>
      <article>
        <label><input type="radio" name="listType" value="order" checked> 번호형</label>
        <label><input type="radio" name="listType" value="bullet"> 기호형</label>
      </article>
      <article>
        <label><input type="radio" name="align" value="left"> 왼쪽 정렬</label>
        <label><input type="radio" name="align" value="center" checked> 가운데 정렬</label>
      </article>
      <article>
        <textarea placeholder="내용을 입력해주세요"></textarea>
      </article>
    </template>
    <!-- 이미지 한장 :: 이미지 & 텍스트+이미지 -->
    <template v-else-if="activeComp === 'comp4'">
      <div class="comp-tit">
        <p>이미지</p>
        <button type="button">이미지 올리기</button>
      </div>
      <article>
        <label><input type="checkbox" name="useText" value="title"> 타이틀 쓰기</label>
        <label><input type="checkbox" name="useText" value="desc"> 설명 쓰기</label>
        <label><input type="checkbox" name="useText" value="imgView"> 이미지 크게 보기 (뷰어)</label>
      </article>
      <article>
        <input type="text" name="imgTitle" placeholder="타이틀 입력">
        <textarea placeholder="내용을 입력하세요"></textarea>
      </article>
    </template>
    <!-- 이미지 여러장 :: 이미지 + 텍스트 -->
    <template v-else-if="activeComp === 'comp5'">
      <div class="comp-tit">
        <p>이미지 여러 장</p>
        <button type="button">이미지 올리기</button>
      </div>
      <article>
        <label><input type="radio" name="alignType" value="imgLeft"> 이미지 왼쪽</label>
        <label><input type="radio" name="alignType" value="imgRight"> 이미지 오른쪽</label>
        <label><input type="radio" name="alignType" value="imgOne"> 1단 이미지</label>
        <label><input type="radio" name="alignType" value="imgTwo"> 2단 이미지</label>
      </article>
      <article>
        <label><input type="checkbox" name="useText" value="title"> 타이틀 쓰기</label>
        <label><input type="checkbox" name="useText" value="desc"> 설명 쓰기</label>
        <label><input type="checkbox" name="useText" value="imgView"> 이미지 크게 보기 (뷰어)</label>
      </article>
      <article>
        <input type="text" name="imgTitle" placeholder="타이틀 입력">
        <textarea placeholder="내용을 입력하세요"></textarea>
      </article>
    </template>
    <!-- 이미지 여러장 :: 이미지 -->
    <template v-else-if="activeComp === 'comp6'">
      <div class="comp-tit">
        <p>이미지 여러 장</p>
        <button type="button">이미지 올리기</button>
      </div>
      <article>
        <label><input type="radio" name="alignType" value="imgOne" checked> 1단 이미지</label>
        <label><input type="radio" name="alignType" value="imgTwo"> 2단 이미지</label>
        <label><input type="radio" name="alignType" value="imgThree"> 3단 이미지</label>
      </article>
      <article>
        <input type="text" name="imgTitle" placeholder="타이틀">
      </article>
    </template>
    <!-- 지도 -->
    <template v-else-if="activeComp === 'comp7'">
      <div class="comp-tit">
        <p>지도</p>
        <button type="button">지도에서 위치 선택</button>
      </div>
      <article>
        <input type="text" name="pivotName" placeholder="업체명을 입력해 주세요">
        <input type="text" name="pivotAddr" placeholder="주소를 입력해 주세요">
      </article>
    </template>
    <!-- 구분선 -->
    <template v-else-if="activeComp === 'comp8'">
      <div class="comp-tit">
        <p>구분선</p>
      </div>
      <article>
        <label><input type="radio" name="lineType" value="blank" checked> 공백</label>
        <label><input type="radio" name="lineType" value="solid"> 실선</label>
        <label><input type="radio" name="lineType" value="dotted"> 실선</label>
      </article>
    </template>
  </div>
</template>
<script>
  export default {
    name: "edit-frame",
    data () {
      return {
        activeComp: 'comp5'
      }
    }
  }
</script>

<style scoped>
  .edit-frame { width:540px; max-height:614px; border:1px solid #e2e4e5;}
  .edit-frame .comp-tit { padding:1rem;}
  .edit-frame .comp-tit p { display:inline-block; font-size:1.15rem; font-weight:bold; vertical-align:middle;}
  .edit-frame .comp-tit button { margin-left:6px; padding:0 8px; border:1px solid #d9dbdc; color:#58595d; font-size:.8rem; line-height:25px; letter-spacing:-.5px; vertical-align:middle;}
  .edit-frame article { padding:1rem; border-top:1px solid #f3f3f3;}
  .edit-frame input[type='text'] { width:100%; padding:.5rem 1rem; border:1px solid #e3e4e4;}
  .edit-frame textarea { width:100%; height:80px; padding:1rem; border:1px solid #e3e4e4;}
</style>
