<template>
  <!-- 타이틀 -->
  <div v-if="compObj.type === 'cTITLE'">
    <div class="comp-tit">
      <p>{{compObj.title ? compObj.title : '타이틀'}}</p>
    </div>
    <article>
      <label><input type="radio" v-model="compObj.size" value="small"> 작게</label>
      <label><input type="radio" v-model="compObj.size" value="lazy"> 크게</label>
    </article>
    <article>
      <label><input type="radio" v-model="compObj.align" value="left"> 왼쪽 정렬</label>
      <label><input type="radio" v-model="compObj.align" value="center"> 가운데 정렬</label>
    </article>
    <article>
      <textarea placeholder="타이틀을 입력해주세요" v-model="compObj.value"></textarea>
    </article>
  </div>
  <!-- 텍스트 -->
  <div v-else-if="compObj.type === 'cTXT'">
    <div class="comp-tit">
      <p>{{compObj.title ? compObj.title : '텍스트'}}</p>
    </div>
    <article>
      <label><input type="radio" v-model="compObj.txtType" value="body"> 본문형</label>
      <label><input type="radio" v-model="compObj.txtType" value="list"> 목록형</label>
    </article>
    <article v-if="compObj.txtType === 'list'">
      <label><input type="radio" v-model="compObj.listType" value="order" checked> 번호형</label>
      <label><input type="radio" v-model="compObj.listType" value="bullet"> 기호형</label>
    </article>
    <article>
      <label><input type="radio" v-model="compObj.align" value="left"> 왼쪽 정렬</label>
      <label><input type="radio" v-model="compObj.align" value="center"> 가운데 정렬</label>
    </article>
    <article>
      <textarea placeholder="내용을 입력해주세요"></textarea>
    </article>
  </div>
  <!-- 이미지 한장 :: 이미지 & 텍스트+이미지 -->
  <div v-else-if="compObj.type === 'cIMG'">
    <div class="comp-tit">
      <p>{{compObj.title ? compObj.title : '이미지 한장'}}</p>
      <!--<button type="button">이미지 올리기</button>-->
    </div>
    <input type="file" @change="imgFileSync">
    <article>
      <label><input type="checkbox" v-model="compObj.useTitle"> 타이틀 쓰기</label>
      <label><input type="checkbox" v-model="compObj.useDesc"> 설명 쓰기</label>
      <label><input type="checkbox" v-model="compObj.useView"> 이미지 크게 보기 (뷰어)</label>
    </article>
    <article v-if="compObj.useTitle || compObj.useText">
      <input type="text" v-if="compObj.useTitle" v-model="compObj.imgTitle" placeholder="타이틀 입력">
      <textarea v-if="compObj.useDesc" v-model="compObj.imgDesc" placeholder="내용을 입력하세요"></textarea>
    </article>
  </div>
  <!-- 이미지 여러장 :: 이미지 + 텍스트 -->
  <div v-else-if="compObj.type === 'cTXTIMGS'">
    <div class="comp-tit">
      <p>{{compObj.title ? compObj.title : '이미지 여러장'}}</p>
    </div>
    <article>
      <label><input type="radio" v-model="compObj.alignType" value="imgLeft"> 이미지 왼쪽</label>
      <label><input type="radio" v-model="compObj.alignType" value="imgRight"> 이미지 오른쪽</label>
      <label><input type="radio" v-model="compObj.alignType" value="imgOne"> 1단 이미지</label>
      <label><input type="radio" v-model="compObj.alignType" value="imgTwo"> 2단 이미지</label>
    </article>
    <article>
      <label><input type="checkbox" v-model="compObj.useTitle"> 타이틀 쓰기</label>
      <label><input type="checkbox" v-model="compObj.useDesc"> 설명 쓰기</label>
      <label><input type="checkbox" v-model="compObj.useView"> 이미지 크게 보기 (뷰어)</label>
    </article>
    <div class="cimg-box" v-for="(item,idx) in compObj.imgs" :key="item.id">
      <article>
        <p>{{idx+1}}번째 이미지</p>
        <input type="file" @change="imgFileSync($event, idx)" />
      </article>
      <article v-if="compObj.useTitle || compObj.useDesc">
        <input type="text" v-if="compObj.useTitle" v-model="item.imgTitle" placeholder="타이틀 입력">
        <textarea v-if="compObj.useDesc" v-model="item.imgDesc" placeholder="내용을 입력하세요"></textarea>
      </article>
    </div>
    <button type="button" @click="cIMG_add(compObj)">이미지 추가</button>
  </div>
  <!-- 이미지 여러장 :: 이미지 -->
  <div v-else-if="compObj.type === 'cIMGS'">
    <div class="comp-tit">
      <p>{{compObj.title ? compObj.title : '이미지 여러장'}}</p>
    </div>
    <div class="cimg-box" v-for="(item,idx) in compObj.imgs" :key="item.id">
      <article>
        <p>{{idx+1}}번째 이미지</p>
        <input type="file" @change="imgFileSync($event, idx)" />
      </article>
    </div>
    <button type="button" @click="cIMG_add">이미지 추가</button>
    <article>
      <label><input type="radio" v-model="compObj.alignType" value="imgOne" checked> 1단 이미지</label>
      <label><input type="radio" v-model="compObj.alignType" value="imgTwo"> 2단 이미지</label>
      <label><input type="radio" v-model="compObj.alignType" value="imgThree"> 3단 이미지</label>
    </article>
    <article>
      <input type="text" v-model="compObj.imgTitle" placeholder="타이틀">
    </article>
  </div>
  <!-- 지도: 미설계 -->
  <div v-else-if="compObj.type === 'cMAP'">
    <div class="comp-tit">
      <p>{{compObj.title ? compObj.title : '지도'}}</p>
      <button type="button">지도에서 위치 선택</button>
    </div>
    <article>
      <input type="text" name="pivotName" placeholder="업체명을 입력해 주세요">
      <input type="text" name="pivotAddr" placeholder="주소를 입력해 주세요">
    </article>
  </div>
  <!-- 구분선 -->
  <div v-else-if="compObj.type === 'cLINE'">
    <div class="comp-tit">
      <p>{{compObj.title ? compObj.title : '구분선'}}</p>
    </div>
    <article>
      <label><input type="radio" v-model="compObj.lineType" value="blank"> 공백</label>
      <label><input type="radio" v-model="compObj.lineType" value="solid"> 실선</label>
      <label><input type="radio" v-model="compObj.lineType" value="dotted"> 점선</label>
    </article>
  </div>
</template>

<script>
  export default {
    name: "detail-set",
    props: {
      compObj : Object
    },
    methods: {
      cIMG_add () {
        let resObj = {}
        switch (this.compObj.type) {
          case 'cTXTIMGS' :
            resObj = {
              id: this.compObj.id + "_" + new Date().getTime(), // 이미지 여러장 컴포넌트 내 단일 이미지컴포넌트 ID
              img: '', // 이미지 경로 값
              imgTitle: '',  // 이미지 타이틀 입력 문구
              imgDesc: '',  // 이미지 설명 입력 문구
            }
            break
          case 'cIMGS' :
            resObj = {
              id: this.compObj.id + "_" + new Date().getTime(), // 이미지 여러장 컴포넌트 내 단일 이미지컴포넌트 ID
              img: '', // 이미지 경로 값
            }
            break
        }
        this.$emit('cIMG_add', resObj)
      },
      imgFileSync ($event, idx) {
        //console.log($event.target.files[0].name)
        this.$emit('imgFileSync', $event.target.files[0], idx)
      }
    }
  }
</script>

<style scoped>

</style>
