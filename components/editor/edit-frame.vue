<!--suppress ALL -->
<template>
  <!-- Component Detail Setting -->
  <div class="edit-frame">
    <!-- 테스트 버튼 : 삭제 예정 -->
    <div class="comp-test" style="margin-bottom:30px;">
      <button type="button" @click="activeCompId = 'comp1'">타이틀</button>
      <button type="button" @click="activeCompId = 'comp2'">본문형 텍스트</button>
      <button type="button" @click="activeCompId = 'comp3'">이미지 한장</button>
      <button type="button" @click="activeCompId = 'comp4'">이미지 여러장 :: 이미지 + 텍스트</button>
      <button type="button" @click="activeCompId = 'comp5'">이미지 여러장 :: 이미지</button>
      <button type="button" @click="activeCompId = 'comp6'">지도</button>
      <button type="button" @click="activeCompId = 'comp7'">구분선</button>
    </div>
    <!-- 테스트 버튼 : 삭제 예정 [e] -->
    <!-- 요소 상세 설정 컴포넌트 -->
    <detail-set :compObj ="targetComp"
                @cIMG_add="cIMG_add"
                @imgFileSync="imgFileSync"
    />
    <pre>{{targetComp}}</pre>
  </div>
</template>
<script>
  import detailSet from '~/components/detail-set'
  export default {
    name: "edit-frame",
    components:{detailSet},
    data () {
      return {
        activeCompId: 'comp5',
        comps: [
          {
            /* 공통 */
            id: 'comp1',
            type: 'cTITLE', // 요소 타입
            title: '타이틀', // 요소 타이틀 (기본값 각자 지정되어 있음)
            /* 개별 */
            size: 'lazy', // lazy(크게), small(작게) [ 기본값: lazy ]
            align: 'left', // left(왼쪽), center(가운데) [ 기본값: left ]
            value: '', // 타이틀에 입력 할 문구
          },{
            /* 공통 */
            id: 'comp2',
            type: 'cTXT', // 요소 타입
            title: '텍스트', // 요소 타이틀 (기본값 각자 지정되어 있음)
            /* 개별 */
            txtType: 'body', // body(본문형), list(목록형) [ 기본값: main ]
            listType: 'order', // order(번호형), bullet(기호형) [ 기본값: order ]
            align: 'left', // left(왼쪽), center(가운데) [ 기본값: left ]
          },{
            /* 공통 */
            id: 'comp3',
            type: 'cIMG', // 요소 타입
            title: '이미지 한장', // 요소 타이틀 (기본값 각자 지정되어 있음)
            /* 개별 */
            img: '', // 이미지 경로 값
            useTitle: false, // 타이틀 쓰기 (기본값 false)
            imgTitle: '',  // 이미지 타이틀 입력 문구
            useDesc: false, // 타이틀 쓰기 (기본값 false)
            imgDesc: '',  // 이미지 설명 입력 문구
            useView: false, // 이미지 크게보기 (기본값 false)
          },{
            /* 공통 */
            id: 'comp4',
            type: 'cTXTIMGS', // 요소 타입
            title: '이미지 여러장', // 요소 타이틀 (기본값 각자 지정되어 있음)
            /* 개별 */
            alignType: 'imgLeft',  // imgLeft(이미지 왼쪽), imgRight(이미지 오른쪽), imgOne(이미지 1단), imgTwo(이미지 2단) [ 기본값: imgLeft ]
            useTitle: false, // 이미지 타이틀 쓰기 (기본값 false)
            useDesc: false, // 이미지 설명 쓰기 (기본값 false)
            useView: false, // 이미지 크게보기 (기본값 false)
            imgs: [{
              id: 'comp4_1', // 이미지 여러장 컴포넌트 내 단일 이미지컴포넌트 ID
              img: '', // 이미지 경로 값
              imgTitle: '',  // 이미지 타이틀 입력 문구
              imgDesc: '',  // 이미지 설명 입력 문구
            },{
              id: 'comp4_2', // 이미지 여러장 컴포넌트 내 단일 이미지컴포넌트 ID
              img: '', // 이미지 경로 값
              imgTitle: '',  // 이미지 타이틀 입력 문구
              imgDesc: '',  // 이미지 설명 입력 문구
            }]
          },{
            /* 공통 */
            id: 'comp5',
            type: 'cIMGS', // 요소 타입
            title: '이미지 여러장', // 요소 타이틀 (기본값 각자 지정되어 있음)
            /* 개별 */
            alignType: 'imgOne',  // imgOne(1단), twoOne(2단), threeOne(3단) [ 기본값: imgOne ]
            imgTitle: '',  // 이미지 타이틀 입력 문구
            imgs: [{
              id: 'comp5_1', // 이미지 여러장 컴포넌트 내 단일 이미지컴포넌트 ID
              img: '', // 이미지 경로 값
            },{
              id: 'comp5_2', // 이미지 여러장 컴포넌트 내 단일 이미지컴포넌트 ID
              img: '', // 이미지 경로 값
            }]
          },{
          // 미설계 : 속성 확인 필요
            id: 'comp6',
            type: 'cMAP', // 요소 타입
            title: '지도' // 요소 타이틀 (기본값 각자 지정되어 있음)
          },{
            /* 공통 */
            id: 'comp7',
            type: 'cLINE', // 요소 타입
            title: '구분선', // 요소 타이틀 (기본값 각자 지정되어 있음)
            /* 개별 */
            lineType: 'blank' // blank(공백), solid(실선), dotted(점선)
          },
        ]
      }
    },
    computed: {
      targetComp: function () {
        return this.comps.filter((comp)=>{return comp.id === this.activeCompId})[0]
      }
    },
    methods: {
      cIMG_add (new_cIMGS) {
        //console.log('new',new_cIMGS)
        this.targetComp.imgs.push(new_cIMGS)
      },
      imgFileSync (file, idx) {
        //console.log('file',file)
        //console.log('idx',idx)
        if (this.targetComp.type === 'cIMG') this.targetComp.img = file.name
        else if (this.targetComp.type === 'cIMGS' || this.targetComp.type === 'cTXTIMGS') this.targetComp.imgs[idx].img = file.name
      }
    }
  }
</script>

<style>
  .edit-frame { width:540px; max-height:614px; border:1px solid #e2e4e5;}
  .edit-frame .comp-tit { padding:1rem;}
  .edit-frame .comp-tit p { display:inline-block; font-size:1.15rem; font-weight:bold; vertical-align:middle;}
  .edit-frame .comp-tit button { margin-left:6px; padding:0 8px; border:1px solid #d9dbdc; color:#58595d; font-size:.8rem; line-height:25px; letter-spacing:-.5px; vertical-align:middle;}
  .edit-frame article { padding:1rem; border-top:1px solid #f3f3f3;}
  .edit-frame input[type='text'] { width:100%; padding:.5rem 1rem; border:1px solid #e3e4e4;}
  .edit-frame textarea { width:100%; height:80px; padding:1rem; border:1px solid #e3e4e4;}
</style>
