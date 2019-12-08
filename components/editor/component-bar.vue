<template>
  <div id="sideBar">
    <p class="sideBarTit">구성요소 추가</p>
    <ul class="sideBarlist1">
      <li>
        <li-comp type="liDepth1">타이틀</li-comp>
        <ul class="sideBarlist2">
          <li><li-comp type="liDepth2">타이틀 텍스트</li-comp></li>
          <li><li-comp type="liDepth2">본문형 텍스트</li-comp></li>
          <li><li-comp type="liDepth2">목록형 텍스트</li-comp></li>
        </ul>
      </li>
      <li>
        <li-comp type="liDepth1">이미지</li-comp>
        <ul class="sideBarlist2">
          <li><li-comp type="liDepth2">이미지</li-comp></li>
          <li><li-comp type="liDepth2">텍스트 + 이미지</li-comp></li>
          <li><li-comp type="liDepth2">좌측이미지 + 텍스트</li-comp></li>
          <li><li-comp type="liDepth2">우측이미지 + 텍스트</li-comp></li>
        </ul>
      <li>
        <li-comp type="liDepth1">지도</li-comp>
        <ul class="sideBarlist2">
          <li><li-comp type="liDepth2">지도</li-comp></li>
        </ul>
      </li>
      <li>
        <li-comp type="liDepth1">버튼</li-comp>
        <ul class="sideBarlist2">
          <li><li-comp type="liDepth2">네모버튼</li-comp></li>
          <li><li-comp type="liDepth2">막대버튼</li-comp></li>
        </ul>
      </li>
      <li>
        <li-comp type="liDepth1">표</li-comp>
        <ul class="sideBarlist2">
          <li><li-comp type="liDepth2">표</li-comp></li>
        </ul>
      </li>
      <li>
        <li-comp type="liDepth1">동영상</li-comp>
        <ul class="sideBarlist2">
          <li><li-comp type="liDepth2">동영상주소</li-comp></li>
        </ul>
      </li>
      <li>
        <li-comp type="liDepth1">구분선</li-comp>
        <ul class="sideBarlist2">
          <li><li-comp type="liDepth2">공백</li-comp></li>
          <li><li-comp type="liDepth2">실선</li-comp></li>
          <li><li-comp type="liDepth2">점선</li-comp></li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script type="JavaScript" src="https://cdnjs.cloudflare.com/ajax/libs/vue/1.0.18/vue.min.js"></script>
<script>
  import liComp from '~/components/common/li-comp.vue'
  export default {
    components: {
      'liComp' : liComp
    },
    name: "component-bar"
  }

</script>

<style lang="css" scoped>

#sideBar { position:absolute; width:200px; min-height:500px; background:#fff; margin-right:20px; border:1px solid #d7d7d7;}
.sideBarTit { position:relative; width:100%; height:44px; background:#eee; padding-left:15px; line-height:44px; font-weight:600; }
.sideBarlist1,.sideBarlist2  { position:relative; width:100%; height:auto; }
.sideBarlist1 > li { position:relative; width:100%; border-bottom:1px solid #e5e5e5; line-height:40px; }
.sideBarlist1 > li > ul { max-height:0; overflow:hidden; transition: all 0.5s ease-out -0.3s;}
.sideBarlist1 > li > a { position:relative; display:inline-block; width:100%; color:#000; text-decoration:none; padding-left:15px; font-size:13px;}
.sideBarlist1 > li > a.on + ul.sideBarlist2 { max-height:1000px; transition: all 0.5s ease-in; }
.sideBarlist1 > li > a > span { position:absolute; right:30px; top:12px; display:inline-block; width:15px; height:15px; }
.sideBarlist1 > li > a > span.arrowDown { background:url('~@/assets/images/arrowDown.png') no-repeat no-repeat center; background-size:15px; }
.sideBarlist1 > li > a > span.arrowUp { background:url('~@/assets/images/arrowUp.png') no-repeat no-repeat center; background-size:15px; }
.sideBarlist2 > li { position:relative; width:100%; border-top:1px solid #e5e5e5; line-height:40px; background:#f6f7f7; }
.sideBarlist2 > li > a { position:relative; display:inline-block; width:100%; color:#777; font-size:13px; text-decoration:none; padding-left:25px; }
.sideBarlist2 > li > a > span { position:absolute; right:30px; top:12px; display:inline-block; width:15px; height:15px; }
.sideBarlist2 > li > a > span.on { background:url('~@/assets/images/plusOn.png') no-repeat no-repeat center; background-size:12px; }
.sideBarlist2 > li > a > span.off { background:url('~@/assets/images/plusOff.png') no-repeat no-repeat center; background-size:12px; }

</style>
