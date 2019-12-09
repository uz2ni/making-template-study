<template>
  <span>
    <span v-if="!editing">
      <span class='text' @click="enableEditing">{{value}}</span>
    </span>
    <span v-if="editing">
      <input ref="myInput" v-model="tempValue" @blur="saveEdit" class="input"/>
    </span>
  </span>
</template>

<script>
  export default {
    name: "editable-text",
    props: ['default'],
    data() {
      return {
        value: this.initValue(),
        tempValue: null,
        editing: false
      }
    },
    methods: {
      initValue: function() {
        if(this.default === undefined || this.default.trim() === "") return "default Editable Text";
        else return this.default.trim();
      },
      enableEditing: function(e){
        this.tempValue = this.value;
        this.editing = true;
        //this.$refs.myInput.focus();
      },
      disableEditing: function(){
        this.tempValue = null;
        this.editing = false;
      },
      saveEdit: function() {
        if(this.tempValue.trim() !== "") {
          if(this.tempValue !== this.value) {
            this.value = this.tempValue;
          }
          this.disableEditing();
        }else {
          alert('공백 없이 입력하세요.');
          // focus
        }

      }
    }
  }
</script>

<style scoped>
  .input {
    color: black;
  }
</style>
