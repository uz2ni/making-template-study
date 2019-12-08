<template lang="html">
  <!--1Depth list item 화살표형-->
  <a v-if="type=='liDepth1'" v-bind:class="{on: isActive}" @click.prevent="dropToggle">
    <slot></slot><span v-bind:class="{arrowUp : isActive, arrowDown : !isActive}"></span>
  </a>
  <!--//1Depth list item-->
  <a v-else-if="type=='liDepth2'" @click.prevent="addItem">
    <slot></slot><span v-bind:class="{ added : isAdded, unAdded : !isAdded}"></span>
  </a>

</template>

<script>
export default {
  name:"li-comp",
  props:['type'],
  data: function(){
    return {
      dropState: false,
      isActive:false,
      isAdded:false
    }
  },
  methods: {
    dropToggle () {
      if(this.isActive){
        console.log("off");
        this.isActive = !this.isActive;
      }else{
        console.log("on");
        this.isActive = !this.isActive;
      }
    },
    addItem () { //아이템 추가방식 고려 후 수정 필요
      if(this.isAdded){
        console.log("Item Add Stop!");
        this.isAdded = !this.isAdded;
      }else{
        console.log("Item Added!");
        this.isAdded = !this.isAdded;
      }
    }
  }
}
</script>

<style lang="css" scoped>
span.arrowDown { background:url('~@/assets/images/arrowDown.png') no-repeat no-repeat center; background-size:15px; }
span.arrowUp { background:url('~@/assets/images/arrowUp.png') no-repeat no-repeat center; background-size:15px; }
a > span { position:absolute; right:30px; top:12px; display:inline-block; width:15px; height:15px; }
span.added { background:url('~@/assets/images/plusOn.png') no-repeat no-repeat center; background-size:12px; }
span.unAdded { background:url('~@/assets/images/plusOff.png') no-repeat no-repeat center; background-size:12px; }
</style>
