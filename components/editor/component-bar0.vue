<template> <!--이전 버전 백업-->
  <div id="sideBar">
    <p class="sideBarTit">구성요소 추가</p>
    <ul class="sideBarlist1">
      <li>
        <a href="#" @click.prevent="active1 = !active1">텍스트<span class="arrowDown" v-show="!active1"></span><span class="arrowUp" v-show="active1"></span></a>
        <ul class="sideBarlist2" v-show="active1">
          <li><a href="#">타이틀 텍스트<span class="off"></span></a></li>
          <li><a href="#">본문형 텍스트<span class="off"></span></a></li>
          <li><a href="#">목록형 텍스트<span class="off"></span></a></li>
        </ul>
      </li>
      <li>
        <a href="#" @click.prevent="active2 = !active2">이미지<span class="arrowDown" v-show="!active2"></span><span class="arrowUp" v-show="active2"></span></a>
        <ul class="sideBarlist2" v-show="active2">
          <li><a href="#">이미지<span class="off"></span></a></li>
          <li><a href="#">텍스트 + 이미지<span class="off"></span></a></li>
          <li><a href="#">좌측이미지 + 텍스트<span class="off"></span></a></li>
          <li><a href="#">우측이미지 + 텍스트<span class="off"></span></a></li>
        </ul>
      <li>
        <a href="#" @click.prevent="active3 = !active3">지도<span class="arrowDown" v-show="!active3"></span><span class="arrowUp" v-show="active3"></span></a>
        <ul class="sideBarlist2" v-show="active3">
          <li><a href="#">지도<span class="off"></span></a></li>
        </ul>
      </li>
      <li>
        <a href="#" @click.prevent="active4 = !active4">버튼<span class="arrowDown" v-show="!active4"></span><span class="arrowUp" v-show="active4"></span></a>
        <ul class="sideBarlist2" v-show="active4">
          <li><a href="#">네모버튼<span class="off"></span></a></li>
          <li><a href="#">막대버튼<span class="off"></span></a></li>
        </ul>
      </li>
      <li>
        <a href="#" @click.prevent="active5 = !active5">표<span class="arrowDown" v-show="!active5"></span><span class="arrowUp" v-show="active5"></span></a>
        <ul class="sideBarlist2" v-show="active5">
          <li><a href="#">표<span class="off"></span></a></li>
        </ul>
      </li>
      <li>
        <a href="#" @click.prevent="active6 = !active6">동영상<span class="arrowDown" v-show="!active6"></span><span class="arrowUp" v-show="active6"></span></a>
        <ul class="sideBarlist2" v-show="active6">
          <li><a href="#">동영상주소<span class="off"></span></a></li>
        </ul>
      </li>
      <li>
        <a href="#" @click.prevent="active7 = !active7">구분선<span class="arrowDown" v-show="!active7"></span><span class="arrowUp" v-show="active7"></span></a>
        <ul class="sideBarlist2" v-show="active7">
          <li><a href="#">공백<span class="off"></span></a></li>
          <li><a href="#">실선<span class="off"></span></a></li>
          <li><a href="#">점선<span class="off"></span></a></li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script type="JavaScript" src="https://cdnjs.cloudflare.com/ajax/libs/vue/1.0.18/vue.min.js"></script>
<script>
  export default {
    name: "component-bar",
    data:function() {
      return {
        active1: false,
        active2: false,
        active3: false,
        active4: false,
        active5: false,
        active6: false,
        active7: false,
      }
    }
  }

</script>

<style scoped>

#sideBar { position:absolute; width:200px; min-height:500px; background:#fff; margin-right:20px; border:1px solid #d7d7d7;}
.sideBarTit { position:relative; width:100%; height:44px; background:#eee; padding-left:15px; line-height:44px; font-weight:600; }
.sideBarlist1,.sideBarlist2  { position:relative; width:100%; height:auto; }
.sideBarlist1 > li { position:relative; width:100%; border-bottom:1px solid #e5e5e5; line-height:40px;  }
.sideBarlist1 > li > a { position:relative; display:inline-block; width:100%; color:#000; text-decoration:none; padding-left:15px; font-size:13px;}
.sideBarlist1 > li > a > span { position:absolute; right:30px; top:12px; display:inline-block; width:15px;
  height:15px; }
.sideBarlist1 > li > a > span.arrowDown { background:url('~@/assets/images/arrowDown.png') no-repeat no-repeat center; background-size:15px; }
.sideBarlist1 > li > a > span.arrowUp { background:url('~@/assets/images/arrowUp.png') no-repeat no-repeat center; background-size:15px; }
.sideBarlist2 > li { position:relative; width:100%; border-top:1px solid #e5e5e5; line-height:40px; background:#f6f7f7; }
.sideBarlist2 > li > a { position:relative; display:inline-block; width:100%; color:#777; font-size:13px; text-decoration:none; padding-left:25px; }
.sideBarlist2 > li > a > span { position:absolute; right:30px; top:12px; display:inline-block; width:15px; height:15px; }
.sideBarlist2 > li > a > span.on { background:url('~@/assets/images/plusOn.png') no-repeat no-repeat center; background-size:12px; }
.sideBarlist2 > li > a > span.off { background:url('~@/assets/images/plusOff.png') no-repeat no-repeat center; background-size:12px; }

</style>
